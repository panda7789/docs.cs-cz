---
title: "Přístup k formulářům aplikace (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b029ce984f9cef540087181a83070b0c8aa8132
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="0e155-102">Přístup k formulářům aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e155-102">Accessing Application Forms (Visual Basic)</span></span>
<span data-ttu-id="0e155-103">`My.Forms` Objekt poskytuje snadný přístup k instanci jednotlivých formulářů Windows deklarovány v projektu.</span><span class="sxs-lookup"><span data-stu-id="0e155-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="0e155-104">Můžete také použít vlastnosti `My.Application` objektu pro přístup k aplikace úvodní obrazovku a hlavní formulář a získejte seznam otevřete formulářů aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e155-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="0e155-105">Úlohy</span><span class="sxs-lookup"><span data-stu-id="0e155-105">Tasks</span></span>  
 <span data-ttu-id="0e155-106">V následující tabulce jsou uvedeny příklady znázorňující způsob pro přístup k formulářům aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e155-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="0e155-107">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="0e155-107">To</span></span>|<span data-ttu-id="0e155-108">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="0e155-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="0e155-109">Přístup k jednoho formuláře z jiného formuláře v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0e155-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="0e155-110">My.Forms – objekt</span><span class="sxs-lookup"><span data-stu-id="0e155-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="0e155-111">Zobrazení názvů otevřete formulářů všechny aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e155-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="0e155-112">Aktualizujte úvodní obrazovka s informací o stavu spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e155-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="0e155-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e155-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>  
 [<span data-ttu-id="0e155-114">My.Forms – objekt</span><span class="sxs-lookup"><span data-stu-id="0e155-114">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
