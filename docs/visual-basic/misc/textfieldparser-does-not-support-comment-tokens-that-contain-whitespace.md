---
title: TextFieldParser nepodporuje tokeny komentáře obsahující prázdné znaky
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 9a14bc29ecfa917b6213f32cd170aa83d6f60f58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668988"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a><span data-ttu-id="13270-102">TextFieldParser nepodporuje tokeny komentáře obsahující prázdné znaky</span><span class="sxs-lookup"><span data-stu-id="13270-102">TextFieldParser does not support comment tokens that contain white space</span></span>
<span data-ttu-id="13270-103">Byl zadán token komentář, který obsahuje prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="13270-103">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="13270-104">`TextFieldParser` Nepodporuje tokeny komentáře obsahující prázdné znaky, pokud prázdné místo nastane na začátku token.</span><span class="sxs-lookup"><span data-stu-id="13270-104">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="13270-105">Prázdné znaky, ke kterým dochází na začátku token se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="13270-105">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13270-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="13270-106">To correct this error</span></span>  
  
- <span data-ttu-id="13270-107">Zadejte správný komentáři tokenu.</span><span class="sxs-lookup"><span data-stu-id="13270-107">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13270-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13270-108">See also</span></span>

- [<span data-ttu-id="13270-109">TextFieldParser.CommentTokens Property</span><span class="sxs-lookup"><span data-stu-id="13270-109">TextFieldParser.CommentTokens Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [<span data-ttu-id="13270-110">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="13270-110">Parsing Text Files with the TextFieldParser Object</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="13270-111">Objekt TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="13270-111">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
