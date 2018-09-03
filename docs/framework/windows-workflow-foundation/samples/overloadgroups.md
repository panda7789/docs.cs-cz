---
title: OverloadGroups
ms.date: 03/30/2017
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
ms.openlocfilehash: 0773e76d36b25ad5485cc8912c7012815412de9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469866"
---
# <a name="overloadgroups"></a><span data-ttu-id="c3921-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="c3921-102">OverloadGroups</span></span>
<span data-ttu-id="c3921-103">Tento příklad se skládá z aktivity (`CreateLocation`), která má dvě zajímavé vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c3921-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="c3921-104">Některé vyžaduje se argumentů a některé volitelné ty.</span><span class="sxs-lookup"><span data-stu-id="c3921-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="c3921-105">Umožňuje uživateli zvolit poskytnout dvě různé sady argumentů.</span><span class="sxs-lookup"><span data-stu-id="c3921-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="c3921-106">Tyto chování můžete provést pomocí těchto dvou funkcí:</span><span class="sxs-lookup"><span data-stu-id="c3921-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="c3921-107">`[isRequired]` ověřuje, že vlastnost konkrétní aktivity je přiřadit, a pokud ne, dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="c3921-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="c3921-108">`[OverloadGroup]` umístí společně sadu argumentů, abyste uživatele aktivity můžete zvolit použití jedné sady nebo jiného.</span><span class="sxs-lookup"><span data-stu-id="c3921-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="c3921-109">Uživatele nelze použít argumenty z různých skupin přetížit ve stejné instanci.</span><span class="sxs-lookup"><span data-stu-id="c3921-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="c3921-110">Po nastavení různých pracovních postupů, volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> který vrátí hodnotu <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.Constraint>.</span><span class="sxs-lookup"><span data-stu-id="c3921-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.Constraint>.</span></span> <span data-ttu-id="c3921-111">Tisk <xref:System.Activities.Validation.Constraint> objekty do konzoly.</span><span class="sxs-lookup"><span data-stu-id="c3921-111">Print the <xref:System.Activities.Validation.Constraint> objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c3921-112">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="c3921-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c3921-113">Otevřít **OverloadGroups.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3921-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="c3921-114">Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="c3921-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3921-115">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="c3921-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c3921-116">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c3921-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c3921-117">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c3921-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3921-118">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c3921-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
