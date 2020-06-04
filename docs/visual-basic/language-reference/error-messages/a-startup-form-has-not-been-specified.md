---
title: Nebyl zadán formulář spuštění.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 058deb1378ed9218274ae20c8340178f7c8fa58c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409904"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="31981-102">Nebyl zadán formulář spuštění.</span><span class="sxs-lookup"><span data-stu-id="31981-102">A startup form has not been specified</span></span>

<span data-ttu-id="31981-103">Aplikace používá třídu, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> ale neurčuje úvodní formulář.</span><span class="sxs-lookup"><span data-stu-id="31981-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="31981-104">K této chybě může dojít, pokud je v Návrháři projektu zaškrtnuto políčko **Povolit rozhraní aplikace** , ale **formulář spuštění** není zadán.</span><span class="sxs-lookup"><span data-stu-id="31981-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="31981-105">Další informace naleznete na [stránce aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="31981-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="31981-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="31981-106">To correct this error</span></span>  
  
1. <span data-ttu-id="31981-107">Zadejte spouštěcí objekt pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="31981-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="31981-108">Další informace naleznete na [stránce aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="31981-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="31981-109">Přepsat <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodu pro nastavení <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> vlastnosti na úvodní formulář.</span><span class="sxs-lookup"><span data-stu-id="31981-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31981-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="31981-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="31981-111">Přehled aplikačního modelu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31981-111">Overview of the Visual Basic Application Model</span></span>](../../developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
