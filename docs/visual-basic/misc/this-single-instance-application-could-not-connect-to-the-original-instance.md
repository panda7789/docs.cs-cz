---
title: Tato aplikace s jedinou instancí se nemohla připojit k původní instanci.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 04ceec4839d07ba959c39af8c4f582c7abfe7d6b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198126"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="0e0d6-102">Tato aplikace s jedinou instancí se nemohla připojit k původní instanci.</span><span class="sxs-lookup"><span data-stu-id="0e0d6-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="0e0d6-103">Tato aplikace s jedinou instancí se nemohla připojit k původní instanci.</span><span class="sxs-lookup"><span data-stu-id="0e0d6-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="0e0d6-104">Mezi možné příčiny tohoto problému patří následující:</span><span class="sxs-lookup"><span data-stu-id="0e0d6-104">Some of the possible causes for this problem are as follows:</span></span>  
  
- <span data-ttu-id="0e0d6-105">Původní instance přestala reagovat.</span><span class="sxs-lookup"><span data-stu-id="0e0d6-105">The original instance stopped responding.</span></span>  
  
- <span data-ttu-id="0e0d6-106">Aplikace nemá oprávnění k vytváření objektů jádra.</span><span class="sxs-lookup"><span data-stu-id="0e0d6-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="0e0d6-107">Další informace o objektech jádra najdete v tématu [mutexy](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="0e0d6-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="0e0d6-108">Základní název objektů jádra pochází z zřetězení identifikátoru GUID sestavení, hlavní číslo verze a číslo dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="0e0d6-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="0e0d6-109">Základní název může být například `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="0e0d6-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="0e0d6-110">Oprava této chyby při vývoji aplikace</span><span class="sxs-lookup"><span data-stu-id="0e0d6-110">To correct this error when developing the application</span></span>  
  
1. <span data-ttu-id="0e0d6-111">Ověřte, zda aplikace nepřejde do stavu nereagující.</span><span class="sxs-lookup"><span data-stu-id="0e0d6-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2. <span data-ttu-id="0e0d6-112">Ověřte, zda má aplikace dostatečná oprávnění k vytváření objektů jádra.</span><span class="sxs-lookup"><span data-stu-id="0e0d6-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3. <span data-ttu-id="0e0d6-113">Restartujte původní instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e0d6-113">Restart the original instance of the application.</span></span>  
  
4. <span data-ttu-id="0e0d6-114">Restartujte počítač a zrušte tak všechny procesy, které mohou používat prostředek, který je požadován pro připojení k původní instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e0d6-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5. <span data-ttu-id="0e0d6-115">Poznamenejte si okolnosti, za kterých došlo k chybě, a telefonní služby na produkty společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0e0d6-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e0d6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e0d6-116">See also</span></span>

- [<span data-ttu-id="0e0d6-117">Základy ladicího programu</span><span class="sxs-lookup"><span data-stu-id="0e0d6-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-feature-tour)
