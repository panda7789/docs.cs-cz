---
title: "Nelze se připojit k původní instance této aplikace s jedinou instancí"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cb8cef696ba93f922dfe0d92195a5fb5147b4cc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="a7c48-102">Nelze se připojit k původní instance této aplikace s jedinou instancí</span><span class="sxs-lookup"><span data-stu-id="a7c48-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="a7c48-103">Tato aplikace s jedinou instancí se nemohl připojit k původní instance.</span><span class="sxs-lookup"><span data-stu-id="a7c48-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="a7c48-104">Některé možné příčiny tohoto problému jsou následující:</span><span class="sxs-lookup"><span data-stu-id="a7c48-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="a7c48-105">Na původní instanci přestala reagovat.</span><span class="sxs-lookup"><span data-stu-id="a7c48-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="a7c48-106">Aplikace nemá oprávnění k vytváření objektů jádra.</span><span class="sxs-lookup"><span data-stu-id="a7c48-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="a7c48-107">Další informace o objektech jádra najdete v tématu [mutex – třídy](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="a7c48-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="a7c48-108">Základní název pro objekty jádra pochází z zřetězení GUID je sestavení, hlavní číslo verze a číslo podverze.</span><span class="sxs-lookup"><span data-stu-id="a7c48-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="a7c48-109">Například může být základní název `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="a7c48-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="a7c48-110">Chcete-li chybu při vývoji aplikace</span><span class="sxs-lookup"><span data-stu-id="a7c48-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="a7c48-111">Zkontrolujte, jestli aplikace nejde do stavu reagovat.</span><span class="sxs-lookup"><span data-stu-id="a7c48-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="a7c48-112">Zkontrolujte, že aplikace má dostatečná oprávnění k vytváření objektů jádra.</span><span class="sxs-lookup"><span data-stu-id="a7c48-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="a7c48-113">Restartujte původní instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7c48-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="a7c48-114">Restartujte počítač zrušte všechny procesy, které může být prostředek, který je požadován pro připojení k původní instance aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7c48-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="a7c48-115">Poznámka: v případech, za kterých se stala chyba a telefonní služby Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="a7c48-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c48-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7c48-116">See Also</span></span>  
 [<span data-ttu-id="a7c48-117">Základy ladicího programu</span><span class="sxs-lookup"><span data-stu-id="a7c48-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  

