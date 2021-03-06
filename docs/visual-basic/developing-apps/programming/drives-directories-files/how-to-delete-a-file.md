---
title: "방법: Visual Basic에서 파일 삭제"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Delete method
- files, deleting
- files, manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e4b0b87fd403556777e0ab5a1edd517687360374
ms.contentlocale: ko-kr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-delete-a-file-in-visual-basic"></a>방법: Visual Basic에서 파일 삭제
`My.Computer.FileSystem` 개체의 `DeleteFile` 메서드를 사용하면 파일을 삭제할 수 있습니다. 삭제된 파일을 **휴지통**으로 보낼지 여부, 사용자에게 파일 삭제를 확인하는 메시지를 표시할지 여부, 사용자가 작업을 취소할 때 수행할 작업 등의 옵션이 제공됩니다.  
  
### <a name="to-delete-a-text-file"></a>텍스트 파일을 삭제하려면  
  
-   `DeleteFile` 메서드를 사용하여 파일을 삭제합니다. 다음 코드에서는 `test.txt`라는 파일을 삭제하는 방법을 보여 줍니다.  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>텍스트 파일을 삭제하고 사용자에게 파일 삭제를 확인하는 메시지를 표시하려면  
  
-   `showUI`를 `AllDialogs`로 설정하여 `DeleteFile` 메서드를 통해 파일을 삭제합니다. 다음 코드에서는 `test.txt`라는 파일을 삭제하고 사용자가 파일 삭제를 확인할 수 있도록 하는 방법을 보여 줍니다.  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>텍스트 파일을 삭제하고 휴지통으로 보내려면  
  
-   `recycle` 매개 변수에 대해 `SendToRecycleBin`을 지정하여 `DeleteFile` 메서드를 통해 파일을 삭제합니다. 다음 코드에서는 `test.txt`라는 파일을 삭제하고 **휴지통**으로 보내는 방법을 보여 줍니다.  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 다음 조건에서 예외가 발생합니다.  
  
-   길이가 0인 문자열이거나, 공백만 포함하거나, 잘못된 문자를 포함하거나, 경로가 장치 경로인 경우(\\\\.\\로 시작됨)와 같은 여러 가지 이유 중 하나로 경로가 올바르지 않은 경우(<xref:System.ArgumentException>)  
  
-   경로가 `Nothing`이기 때문에 올바르지 않은 경우(<xref:System.ArgumentNullException>)  
  
-   경로가 시스템 정의 최대 길이를 초과하는 경우(<xref:System.IO.PathTooLongException>)  
  
-   경로의 파일 이름이나 폴더 이름에 콜론(:)이 있거나 이름의 형식이 잘못된 경우(<xref:System.NotSupportedException>)  
  
-   파일을 사용 중인 경우(<xref:System.IO.IOException>)  
  
-   경로를 보는 데 필요한 권한이 사용자에게 없는 경우(<xref:System.Security.SecurityException>)  
  
-   파일이 없는 경우(<xref:System.IO.FileNotFoundException>)  
  
-   사용자에게 파일을 삭제할 수 있는 권한이 없거나 파일이 읽기 전용인 경우(<xref:System.UnauthorizedAccessException>)  
  
-   사용자에게 충분한 권한이 없는 부분 신뢰 상황인 경우(<xref:System.Security.SecurityException>)  
  
-   사용자가 작업을 취소하고 `onUserCancel`이 `ThrowException`으로 설정된 경우(<xref:System.OperationCanceledException>)  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.UIOption>   
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>   
 [방법: 디렉터리의 파일 컬렉션 가져오기](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

