---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 24358a1b004f1cefbfeb3fb8451380ed883841df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411470"
---
# <a name="value-visual-basic"></a><span data-ttu-id="6d65d-101">\<value> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d65d-101">\<value> (Visual Basic)</span></span>
<span data-ttu-id="6d65d-102">Určuje popis vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6d65d-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d65d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d65d-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d65d-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d65d-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="6d65d-105">Popis vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6d65d-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d65d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d65d-106">Remarks</span></span>  
 <span data-ttu-id="6d65d-107">Použijte `<value>` značku k popisu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6d65d-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="6d65d-108">Všimněte si, že při přidání vlastnosti pomocí průvodce kódem ve vývojovém prostředí sady Visual Studio bude přidána [\<summary>](summary.md) značka pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6d65d-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](summary.md) tag for the new property.</span></span> <span data-ttu-id="6d65d-109">Měli byste pak ručně přidat `<value>` značku pro popis hodnoty, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="6d65d-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="6d65d-110">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="6d65d-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d65d-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d65d-111">Example</span></span>  
 <span data-ttu-id="6d65d-112">Tento příklad používá `<value>` značku k popisu, jakou hodnotu má `Counter` vlastnost obsahovat.</span><span class="sxs-lookup"><span data-stu-id="6d65d-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6d65d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d65d-113">See also</span></span>

- [<span data-ttu-id="6d65d-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="6d65d-114">XML Comment Tags</span></span>](index.md)
