---
title: "Provádění úloh s objekty My.Application, My.Computer a My.User (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d55e0b3a126f2216d005c7bddbcaefb7d8f0a580
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="38fa6-102">Provádění úloh s objekty My.Application, My.Computer a My.User (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38fa6-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="38fa6-103">Tři ústřední `My` objekty, které poskytují informace a běžně používané funkce jsou `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), a `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span><span class="sxs-lookup"><span data-stu-id="38fa6-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="38fa6-104">Tyto objekty můžete použít pro přístup k informacím, které je aktuální aplikace, počítače, které aplikace se nainstaluje na nebo aktuální uživatel aplikace, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="38fa6-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="38fa6-105">Objekty My.Application, My.Computer a My.User</span><span class="sxs-lookup"><span data-stu-id="38fa6-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="38fa6-106">Následující příklady ukazují, jak mohou být informace načíst pomocí `My`.</span><span class="sxs-lookup"><span data-stu-id="38fa6-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 <span data-ttu-id="38fa6-107">Kromě načítání informací o, členy zveřejněné prostřednictvím tyto tři objekty také umožňují spouštět metody vztahující se na tento objekt.</span><span class="sxs-lookup"><span data-stu-id="38fa6-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="38fa6-108">Například můžete zpřístupnit různé způsoby práce se soubory nebo aktualizovat registr prostřednictvím `My.Computer`.</span><span class="sxs-lookup"><span data-stu-id="38fa6-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="38fa6-109">Soubor vstupně-výstupních operací je výrazně jednodušší a rychlejší s `My`, což zahrnuje celou řadu metod a vlastností pro manipulaci s soubory, adresářů a jednotky.</span><span class="sxs-lookup"><span data-stu-id="38fa6-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="38fa6-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Objekt umožňuje číst z velkých strukturované soubory, které mají oddělovače nebo pole s pevnou šířkou.</span><span class="sxs-lookup"><span data-stu-id="38fa6-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="38fa6-111">Otevře se v tomto příkladu `TextFieldParser``reader` a používá ke čtení `C:\TestFolder1\test1.txt`.</span><span class="sxs-lookup"><span data-stu-id="38fa6-111">This example opens the `TextFieldParser``reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 <span data-ttu-id="38fa6-112">`My.Application`Umožňuje změnit jazykovou verzi pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="38fa6-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="38fa6-113">Následující příklad ukazuje, jak tuto metodu lze volat.</span><span class="sxs-lookup"><span data-stu-id="38fa6-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="38fa6-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="38fa6-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [<span data-ttu-id="38fa6-115">Jak Moje závisí na typu projektu</span><span class="sxs-lookup"><span data-stu-id="38fa6-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
