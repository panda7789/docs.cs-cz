---
title: Provádění úloh s objekty My.Application, My.Computer a My.User (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 0372fbf63f6d12e266674f92225183911aa4ca30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834038"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="87520-102">Provádění úloh s objekty My.Application, My.Computer a My.User (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87520-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="87520-103">Tři centrální `My` objekty, které poskytují přístup k informacím a běžně používané funkce jsou `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), a `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span><span class="sxs-lookup"><span data-stu-id="87520-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="87520-104">Můžete použít tyto objekty se dostat k informacím, která souvisí s aktuální aplikace, počítači, na kterém je aplikace nainstalovaná na nebo aktuálního uživatele aplikace, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="87520-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="87520-105">Objekty My.Application, My.Computer a My.User</span><span class="sxs-lookup"><span data-stu-id="87520-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="87520-106">Následující příklady ukazují, jak informace mohou být načteny pomocí `My`.</span><span class="sxs-lookup"><span data-stu-id="87520-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 <span data-ttu-id="87520-107">Kromě načítání informací o členy zveřejněné prostřednictvím těchto tří objektů umožňují spouštět metody vztahující se na tento objekt.</span><span class="sxs-lookup"><span data-stu-id="87520-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="87520-108">Například můžete zpřístupnit různé druhy metody pro práci se soubory nebo aktualizaci registru, které prostřednictvím `My.Computer`.</span><span class="sxs-lookup"><span data-stu-id="87520-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="87520-109">Soubor vstupně-výstupních operací je výrazně jednodušší a rychlejší při použití `My`, která zahrnuje celou řadu metod a vlastností pro práce se soubory, adresáře a jednotky.</span><span class="sxs-lookup"><span data-stu-id="87520-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="87520-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Objekt umožňuje čtení z velké soubory, které máte oddělených nebo pole s pevnou šířkou.</span><span class="sxs-lookup"><span data-stu-id="87520-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="87520-111">Tento příklad otevře `TextFieldParser` `reader` a používá ke čtení z `C:\TestFolder1\test1.txt`.</span><span class="sxs-lookup"><span data-stu-id="87520-111">This example opens the `TextFieldParser` `reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 <span data-ttu-id="87520-112">`My.Application` Umožňuje změnit jazykové verze pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="87520-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="87520-113">Následující příklad ukazuje, jak tuto metodu lze volat.</span><span class="sxs-lookup"><span data-stu-id="87520-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="87520-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87520-114">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="87520-115">Závislost oboru názvů My na typu projektu</span><span class="sxs-lookup"><span data-stu-id="87520-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
