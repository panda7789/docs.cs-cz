---
title: Nebyl zadán formulář spuštění.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 9af95b397bef4a19654510619cf0864c8ab7b76f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833565"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="9d40c-102">Nebyl zadán formulář spuštění.</span><span class="sxs-lookup"><span data-stu-id="9d40c-102">A startup form has not been specified</span></span>
<span data-ttu-id="9d40c-103">Aplikace používá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> třídy, ale není zadán formulář spuštění.</span><span class="sxs-lookup"><span data-stu-id="9d40c-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="9d40c-104">Tato situace může nastat, pokud **Povolit aplikační framework** v Návrháři projektu je zaškrtnuté políčko ale **úvodní formulář** není zadán.</span><span class="sxs-lookup"><span data-stu-id="9d40c-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="9d40c-105">Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9d40c-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d40c-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9d40c-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="9d40c-107">Zadejte spouštěcí objekt pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9d40c-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="9d40c-108">Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9d40c-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2.  <span data-ttu-id="9d40c-109">Přepsat <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metody nastavte <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> vlastnost formuláře úvodního formuláře.</span><span class="sxs-lookup"><span data-stu-id="9d40c-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d40c-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d40c-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="9d40c-111">Přehled aplikačního modelu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d40c-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
