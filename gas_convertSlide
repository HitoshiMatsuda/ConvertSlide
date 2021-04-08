function main() {
  //固定値
  const presentation = SlidesApp.getActivePresentation();
  const slide = presentation.getSlides()[0];
  const presentationId = presentation.getId();
  const fileName = presentation.getName();
  const format = "jpg";
  const pageId = slide.getObjectId();


  //ログ用
  console.log(fileName);
  console.log(presentationId);
  console.log(pageId);


  //画像化メソッド
  const file = convertPresentation(presentationId, pageId, format);

}


//画像化メソッド
function convertPresentation(presentationId, pageId, format) {
  format = format.toLowerCase();
  let ext = format;//ファイル名の拡張子
  switch (format) {
    case "pptx":
    case "odp":
    case "pdf":
    case "txt":
    case "png":
    case "svg":
      break;
    case "jpg":
    case "jpeg":
      format = "jpeg";
      ext = "jpg";
      break;
    default:
      format = "pptx";
      ext = "pptx"
      break;
  }

  const url = "https://----------------------/d/" + presentationId + "/export/" + format;

  const options = {
    method: "get",
    headers: { "Authorization": "Bearer " + ScriptApp.getOAuthToken() },
    muteHttpExceptions: true
  };

  const response = UrlFetchApp.fetch(url, options);
  const presentaion = SlidesApp.openById(presentationId);
  const folder = DriveApp.getFolderById("----------------------------------------------");
  Logger.log(ext);
  return folder.createFile(response.getBlob()).setName(presentaion.getName() + "." + ext);

}