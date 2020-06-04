---
title: Provádění úloh s objekty My.Application, My.Computer a My.User
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 55961d6857b690fc2726f541df8a5497a3207928
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411691"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="01bc3-102">Provádění úloh s objekty My.Application, My.Computer a My.User (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01bc3-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>

<span data-ttu-id="01bc3-103">Tři centrální `My` objekty, které poskytují přístup k informacím a běžně používaným funkcím, jsou `My.Application` ( <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> ), `My.Computer` ( <xref:Microsoft.VisualBasic.Devices.Computer> ), a `My.User` ( <xref:Microsoft.VisualBasic.ApplicationServices.User> ).</span><span class="sxs-lookup"><span data-stu-id="01bc3-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="01bc3-104">Tyto objekty lze použít pro přístup k informacím, které se vztahují k aktuální aplikaci, počítači, na kterém je aplikace nainstalovaná, nebo aktuálnímu uživateli aplikace, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="01bc3-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="01bc3-105">My. Application, my. Computer a my. User</span><span class="sxs-lookup"><span data-stu-id="01bc3-105">My.Application, My.Computer, and My.User</span></span>  

 <span data-ttu-id="01bc3-106">Následující příklady ukazují, jak lze informace načíst pomocí `My` .</span><span class="sxs-lookup"><span data-stu-id="01bc3-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 <span data-ttu-id="01bc3-107">Kromě načítání informací umožňují členové vystavené prostřednictvím těchto tří objektů také spouštět metody související s tímto objektem.</span><span class="sxs-lookup"><span data-stu-id="01bc3-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="01bc3-108">Můžete například získat přístup k nejrůznějším metodám pro manipulaci se soubory nebo aktualizovat registr do `My.Computer` .</span><span class="sxs-lookup"><span data-stu-id="01bc3-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="01bc3-109">Vstupně-výstupní operace se soubory jsou výrazně snazší a rychlejší `My` , což zahrnuje různé metody a vlastnosti pro práci se soubory, adresáři a jednotkami.</span><span class="sxs-lookup"><span data-stu-id="01bc3-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="01bc3-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser>Objekt umožňuje čtení z velkých strukturovaných souborů, které mají pole s oddělovači nebo s pevnou šířkou.</span><span class="sxs-lookup"><span data-stu-id="01bc3-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="01bc3-111">Tento příklad otevře `TextFieldParser` `reader` a použije ho ke čtení z `C:\TestFolder1\test1.txt` .</span><span class="sxs-lookup"><span data-stu-id="01bc3-111">This example opens the `TextFieldParser` `reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 <span data-ttu-id="01bc3-112">`My.Application`umožňuje změnit jazykovou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="01bc3-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="01bc3-113">Následující příklad ukazuje, jak lze tuto metodu volat.</span><span class="sxs-lookup"><span data-stu-id="01bc3-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="01bc3-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="01bc3-114">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="01bc3-115">Závislost oboru názvů My na typu projektu</span><span class="sxs-lookup"><span data-stu-id="01bc3-115">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
