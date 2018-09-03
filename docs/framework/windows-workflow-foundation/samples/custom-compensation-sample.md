---
title: Ukázková vlastní kompenzace
ms.date: 03/30/2017
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
ms.openlocfilehash: ac141a48f87f5b14f6b528f7b3ceb7fdddeaf2d2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475865"
---
# <a name="custom-compensation-sample"></a><span data-ttu-id="7d9b2-102">Ukázková vlastní kompenzace</span><span class="sxs-lookup"><span data-stu-id="7d9b2-102">Custom Compensation Sample</span></span>
<span data-ttu-id="7d9b2-103">Tento příklad ukazuje způsob použití <xref:System.Activities.Statements.CompensableActivity> a její obslužná rutina kompenzace definovat vlastní kompenzační logiky.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-103">This sample shows how to use <xref:System.Activities.Statements.CompensableActivity> and its compensation handler to define custom compensation logic.</span></span> <span data-ttu-id="7d9b2-104">Scénář modelován v této ukázce je agentura pronájem nákladní vozidlo.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-104">The scenario modeled in this sample is a Truck Rental Agency.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="7d9b2-105">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7d9b2-105">Sample Details</span></span>  
 <span data-ttu-id="7d9b2-106">Kroky simulované jsou:</span><span class="sxs-lookup"><span data-stu-id="7d9b2-106">The steps simulated are:</span></span>  
  
1.  <span data-ttu-id="7d9b2-107">Požadavky uživatelů truck pronájem nabídky pro daného data.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-107">The user requests truck rental quotes for a given date.</span></span>  
  
2.  <span data-ttu-id="7d9b2-108">Budou kontaktovány jako tři truck společnosti a jsou k dispozici tři uvozovky.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-108">Three truck companies are contacted and the three quotes are provided.</span></span>  
  
3.  <span data-ttu-id="7d9b2-109">Uživatel vybere jednu nabídku truck a načte pořadí pomocí platební karty.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-109">The user selects one truck quote and proceeds to order by credit card.</span></span>  
  
4.  <span data-ttu-id="7d9b2-110">Aplikace zruší ostatní dva truck uvozovky.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-110">The application cancels the other two truck quotes.</span></span>  
  
5.  <span data-ttu-id="7d9b2-111">Aplikace se účtuje poplatek za služby, který je nevratný neprémiové účty zrušení v případě 10 dní nebo méně než datum rezervaci.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-111">The application charges a service fee that is non-refundable for non-premium accounts if cancelation happens 10 days or less prior to the reservation date.</span></span>  
  
6.  <span data-ttu-id="7d9b2-112">Aplikace se účtuje poplatek pronájem nákladní vozidlo.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-112">The application charges the truck rental fee.</span></span>  
  
7.  <span data-ttu-id="7d9b2-113">Aplikace čeká na datum rezervaci nebo dokud zákazníkovi se rozhodli zrušit rezervaci, podle toho, co nastane dřív.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-113">The application waits until the reservation date or until the customer decided to cancel the reservation, whichever comes first.</span></span>  
  
8.  <span data-ttu-id="7d9b2-114">Pokud zákazník zruší rezervace, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> vlastní kompenzační logiky bude spouštět podle následujícího postupu:</span><span class="sxs-lookup"><span data-stu-id="7d9b2-114">If the customer cancels the reservation, the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> custom compensation logic runs according to the following logic:</span></span>  
  
    1.  <span data-ttu-id="7d9b2-115">Pokud má zákazník neprémiové účet a pak se stále bude účtovat poplatek za služby; je menší než 10 dní před datem rezervace v opačném případě aplikace náhrad servisní poplatek.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-115">If the customer has a non-premium account and it is less than 10 days prior to the reservation date, then the service fee is still charged; otherwise, the application refunds the service fee.</span></span>  
  
    2.  <span data-ttu-id="7d9b2-116">Zbývající část kompenzovatelné aktivity (nákladní vozidlo pořadí + poplatek pořadí nákladní vozidlo) se spouštějí podle kompenzační logika výchozí, což je odpovídajícím způsobem upravit v obráceném pořadí spouštění.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-116">The rest of the compensable activities (truck order + truck order fee) are run according to the default compensation logic, which is to compensate in reverse order of execution.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7d9b2-117">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="7d9b2-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7d9b2-118">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete řešení CustomCompensation.sln.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomCompensation.sln solution.</span></span> <span data-ttu-id="7d9b2-119">Je umístěn v adresáři \WF\Basic\Compensation\CustomCompensation.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-119">It is located in the \WF\Basic\Compensation\CustomCompensation directory.</span></span>  
  
2.  <span data-ttu-id="7d9b2-120">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-120">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="7d9b2-121">Stisknutím kláves CTRL + F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-121">Press CTRL + F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7d9b2-122">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7d9b2-123">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="7d9b2-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7d9b2-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7d9b2-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7d9b2-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`