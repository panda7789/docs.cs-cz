---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 857ea1ccca4d74daf65bba03845004561afefd55
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348514"
---
# <a name="c-visual-basic"></a><span data-ttu-id="7607f-101">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7607f-101">\<c> (Visual Basic)</span></span>
<span data-ttu-id="7607f-102">Označuje, že text v rámci popisu je kód.</span><span class="sxs-lookup"><span data-stu-id="7607f-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7607f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7607f-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="7607f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="7607f-104">Parameters</span></span>  
  
|<span data-ttu-id="7607f-105">Parametr</span><span class="sxs-lookup"><span data-stu-id="7607f-105">Parameter</span></span>|<span data-ttu-id="7607f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7607f-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="7607f-107">Text, který chcete označit jako kód.</span><span class="sxs-lookup"><span data-stu-id="7607f-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7607f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7607f-108">Remarks</span></span>  
 <span data-ttu-id="7607f-109">Značka `<c>` poskytuje způsob, jak označit, že text v rámci popisu by měl být označen jako kód.</span><span class="sxs-lookup"><span data-stu-id="7607f-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="7607f-110">Použijte [\<> kódu](../../../visual-basic/language-reference/xmldoc/code.md) k označení více řádků jako kódu.</span><span class="sxs-lookup"><span data-stu-id="7607f-110">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="7607f-111">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="7607f-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7607f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7607f-112">Example</span></span>  
 <span data-ttu-id="7607f-113">Tento příklad používá značku `<c>` v části Summary k označení toho, že `Counter` je kód.</span><span class="sxs-lookup"><span data-stu-id="7607f-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7607f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7607f-114">See also</span></span>

- [<span data-ttu-id="7607f-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="7607f-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
