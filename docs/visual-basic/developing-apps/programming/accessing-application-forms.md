---
title: Přístup k formulářům aplikace (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
ms.openlocfilehash: 44942827c4bfbaeffb3e424d8339ac6d001722ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566918"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="d2677-102">Přístup k formulářům aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2677-102">Accessing Application Forms (Visual Basic)</span></span>
<span data-ttu-id="d2677-103">`My.Forms` Objekt, který poskytuje snadný způsob, jak získat přístup instanci jednotlivých formulářů Windows deklarované v projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2677-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="d2677-104">Můžete také použít vlastnosti `My.Application` objektu pro přístup k aplikačním úvodní obrazovky a hlavní formulář a získání seznamu formulářů otevřít v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d2677-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="d2677-105">Úlohy</span><span class="sxs-lookup"><span data-stu-id="d2677-105">Tasks</span></span>  
 <span data-ttu-id="d2677-106">V následující tabulce jsou uvedeny příklady jak získat přístup k formulářům aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2677-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="d2677-107">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="d2677-107">To</span></span>|<span data-ttu-id="d2677-108">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="d2677-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="d2677-109">Jeden formulář z jiného formuláře v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d2677-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="d2677-110">Objekt My.Forms</span><span class="sxs-lookup"><span data-stu-id="d2677-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="d2677-111">Zobrazení názvů všech aplikace otevřít formulářů.</span><span class="sxs-lookup"><span data-stu-id="d2677-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="d2677-112">Aktualizujte úvodní obrazovka s informací o stavu spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2677-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="d2677-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2677-113">See also</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="d2677-114">Objekt My.Forms</span><span class="sxs-lookup"><span data-stu-id="d2677-114">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
