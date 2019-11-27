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
ms.openlocfilehash: 332b6a7563160528b6c17210170af0db6e9bc0e7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349243"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="a6e68-102">Přístup k formulářům aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6e68-102">Accessing Application Forms (Visual Basic)</span></span>

<span data-ttu-id="a6e68-103">Objekt `My.Forms` poskytuje snadný způsob, jak získat přístup k instanci každého formuláře Windows deklarovaného v projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6e68-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="a6e68-104">Můžete také použít vlastnosti objektu `My.Application` pro přístup k úvodní obrazovce aplikace a k hlavnímu formuláři a získat seznam otevřených formulářů aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6e68-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="a6e68-105">Úlohy</span><span class="sxs-lookup"><span data-stu-id="a6e68-105">Tasks</span></span>  

 <span data-ttu-id="a6e68-106">V následující tabulce jsou uvedeny příklady, které ukazují, jak přistupovat k formulářům aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6e68-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="a6e68-107">Do</span><span class="sxs-lookup"><span data-stu-id="a6e68-107">To</span></span>|<span data-ttu-id="a6e68-108">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="a6e68-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="a6e68-109">Přístup k jednomu formuláři z jiného formuláře v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a6e68-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="a6e68-110">Objekt My.Forms</span><span class="sxs-lookup"><span data-stu-id="a6e68-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="a6e68-111">Zobrazí názvy všech otevřených formulářů aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6e68-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="a6e68-112">Aktualizujte úvodní obrazovku o stavové informace při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6e68-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="a6e68-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6e68-113">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="a6e68-114">Objekt My.Forms</span><span class="sxs-lookup"><span data-stu-id="a6e68-114">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
