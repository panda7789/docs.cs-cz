---
title: "Nelze se připojit k původní instance této aplikace s jedinou instancí"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fbc8458231c36f3af9ca4de524e01e19a162ee47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="9dab1-102">Nelze se připojit k původní instance této aplikace s jedinou instancí</span><span class="sxs-lookup"><span data-stu-id="9dab1-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="9dab1-103">Tato aplikace s jedinou instancí se nemohl připojit k původní instance.</span><span class="sxs-lookup"><span data-stu-id="9dab1-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="9dab1-104">Některé možné příčiny tohoto problému jsou následující:</span><span class="sxs-lookup"><span data-stu-id="9dab1-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="9dab1-105">Na původní instanci přestala reagovat.</span><span class="sxs-lookup"><span data-stu-id="9dab1-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="9dab1-106">Aplikace nemá oprávnění k vytváření objektů jádra.</span><span class="sxs-lookup"><span data-stu-id="9dab1-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="9dab1-107">Další informace o objektech jádra najdete v tématu [mutex – třídy](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="9dab1-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="9dab1-108">Základní název pro objekty jádra pochází z zřetězení GUID je sestavení, hlavní číslo verze a číslo podverze.</span><span class="sxs-lookup"><span data-stu-id="9dab1-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="9dab1-109">Například může být základní název `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="9dab1-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="9dab1-110">Chcete-li chybu při vývoji aplikace</span><span class="sxs-lookup"><span data-stu-id="9dab1-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="9dab1-111">Zkontrolujte, jestli aplikace nejde do stavu reagovat.</span><span class="sxs-lookup"><span data-stu-id="9dab1-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="9dab1-112">Zkontrolujte, že aplikace má dostatečná oprávnění k vytváření objektů jádra.</span><span class="sxs-lookup"><span data-stu-id="9dab1-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="9dab1-113">Restartujte původní instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="9dab1-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="9dab1-114">Restartujte počítač zrušte všechny procesy, které může být prostředek, který je požadován pro připojení k původní instance aplikace.</span><span class="sxs-lookup"><span data-stu-id="9dab1-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="9dab1-115">Poznámka: v případech, za kterých se stala chyba a telefonní služby Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="9dab1-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dab1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9dab1-116">See Also</span></span>  
 [<span data-ttu-id="9dab1-117">NIB: Postupy: Specifikace chování vytváření instancí pro aplikaci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9dab1-117">NIB: How to: Specify Instancing Behavior for an Application (Visual Basic)</span></span>](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e)  
 [<span data-ttu-id="9dab1-118">Základy ladicího programu</span><span class="sxs-lookup"><span data-stu-id="9dab1-118">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="9dab1-119">Podpora produktu PAVEOVER a usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="9dab1-119">PAVEOVER Product Support and Accessibility</span></span>](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)
