---
title: Přístup k formulářům aplikace
ms.date: 07/20/2015
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
ms.openlocfilehash: 44f98632fd2fd6c4c087a78b805d5b7da750df87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410202"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="814c9-102">Přístup k formulářům aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="814c9-102">Accessing Application Forms (Visual Basic)</span></span>

<span data-ttu-id="814c9-103">`My.Forms`Objekt poskytuje snadný způsob, jak získat přístup k instanci každého formuláře Windows deklarovaného v projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="814c9-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="814c9-104">Můžete také použít vlastnosti `My.Application` objektu pro přístup k úvodní obrazovce aplikace a k hlavnímu formuláři a získat seznam otevřených formulářů aplikace.</span><span class="sxs-lookup"><span data-stu-id="814c9-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="814c9-105">Úlohy</span><span class="sxs-lookup"><span data-stu-id="814c9-105">Tasks</span></span>  

 <span data-ttu-id="814c9-106">V následující tabulce jsou uvedeny příklady, které ukazují, jak přistupovat k formulářům aplikace.</span><span class="sxs-lookup"><span data-stu-id="814c9-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="814c9-107">Akce</span><span class="sxs-lookup"><span data-stu-id="814c9-107">To</span></span>|<span data-ttu-id="814c9-108">Seznamte se s </span><span class="sxs-lookup"><span data-stu-id="814c9-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="814c9-109">Přístup k jednomu formuláři z jiného formuláře v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="814c9-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="814c9-110">My.Forms – objekt</span><span class="sxs-lookup"><span data-stu-id="814c9-110">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="814c9-111">Zobrazí názvy všech otevřených formulářů aplikace.</span><span class="sxs-lookup"><span data-stu-id="814c9-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="814c9-112">Aktualizujte úvodní obrazovku o stavové informace při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="814c9-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="814c9-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="814c9-113">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="814c9-114">My.Forms – objekt</span><span class="sxs-lookup"><span data-stu-id="814c9-114">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
