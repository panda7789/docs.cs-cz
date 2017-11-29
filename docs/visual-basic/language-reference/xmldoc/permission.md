---
title: "&lt;oprávnění&gt; (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 67e11998e43a43f92c26eb5f7daa488d288823c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="ff333-102">&lt;oprávnění&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff333-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="ff333-103">Určuje požadované oprávnění člena.</span><span class="sxs-lookup"><span data-stu-id="ff333-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff333-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff333-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff333-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff333-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="ff333-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="ff333-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="ff333-107">Kompilátor zkontroluje, zda existuje element daného kódu a překládá `member` na element kanonický název ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="ff333-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="ff333-108">Uzavřete `member` v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="ff333-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ff333-109">Popis přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="ff333-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff333-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff333-110">Remarks</span></span>  
 <span data-ttu-id="ff333-111">Použití `<permission>` značky k dokumentu přístup člena.</span><span class="sxs-lookup"><span data-stu-id="ff333-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="ff333-112">Použití <xref:System.Security.PermissionSet> třídu k určení přístup k členem.</span><span class="sxs-lookup"><span data-stu-id="ff333-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="ff333-113">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="ff333-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff333-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff333-114">Example</span></span>  
 <span data-ttu-id="ff333-115">Tento příklad používá `<permission>` značka, které popisují, které <xref:System.Security.Permissions.FileIOPermission> je požadován `ReadFile` metoda.</span><span class="sxs-lookup"><span data-stu-id="ff333-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ff333-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff333-116">See Also</span></span>  
 [<span data-ttu-id="ff333-117">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="ff333-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
