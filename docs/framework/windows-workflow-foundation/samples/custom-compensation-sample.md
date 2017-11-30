---
title: "Ukázka vlastních kompenzace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 088e8e771d5fea60987e7ac53ebad0d3fef24b5d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="custom-compensation-sample"></a><span data-ttu-id="72d88-102">Ukázka vlastních kompenzace</span><span class="sxs-lookup"><span data-stu-id="72d88-102">Custom Compensation Sample</span></span>
<span data-ttu-id="72d88-103">Tento příklad ukazuje způsob použití <xref:System.Activities.Statements.CompensableActivity> a její obslužnou rutinu kompenzace k definování vlastní kompenzace logiku.</span><span class="sxs-lookup"><span data-stu-id="72d88-103">This sample shows how to use <xref:System.Activities.Statements.CompensableActivity> and its compensation handler to define custom compensation logic.</span></span> <span data-ttu-id="72d88-104">Scénář modelován v této ukázce je agentura pronájem vůz.</span><span class="sxs-lookup"><span data-stu-id="72d88-104">The scenario modeled in this sample is a Truck Rental Agency.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="72d88-105">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="72d88-105">Sample Details</span></span>  
 <span data-ttu-id="72d88-106">Kroky simulated jsou:</span><span class="sxs-lookup"><span data-stu-id="72d88-106">The steps simulated are:</span></span>  
  
1.  <span data-ttu-id="72d88-107">Žádosti uživatelů vůz pronájem uvozovky pro dané datum.</span><span class="sxs-lookup"><span data-stu-id="72d88-107">The user requests truck rental quotes for a given date.</span></span>  
  
2.  <span data-ttu-id="72d88-108">Budou kontaktovány tři vůz společnosti a jsou dostupné tři uvozovky.</span><span class="sxs-lookup"><span data-stu-id="72d88-108">Three truck companies are contacted and the three quotes are provided.</span></span>  
  
3.  <span data-ttu-id="72d88-109">Uživatel vybere jednu nabídku vůz a pokračuje k seřazení s platební karty.</span><span class="sxs-lookup"><span data-stu-id="72d88-109">The user selects one truck quote and proceeds to order by credit card.</span></span>  
  
4.  <span data-ttu-id="72d88-110">Aplikace zruší další dva vůz uvozovky.</span><span class="sxs-lookup"><span data-stu-id="72d88-110">The application cancels the other two truck quotes.</span></span>  
  
5.  <span data-ttu-id="72d88-111">Aplikace účtuje poplatek služby, který je nevratný pro neprémiové účty Pokud zrušení stane 10 dní nebo méně před datem rezervace.</span><span class="sxs-lookup"><span data-stu-id="72d88-111">The application charges a service fee that is non-refundable for non-premium accounts if cancelation happens 10 days or less prior to the reservation date.</span></span>  
  
6.  <span data-ttu-id="72d88-112">Aplikace účtuje poplatek pronájem vůz.</span><span class="sxs-lookup"><span data-stu-id="72d88-112">The application charges the truck rental fee.</span></span>  
  
7.  <span data-ttu-id="72d88-113">Aplikace čeká na datum rezervace nebo dokud zákazník se rozhodli zrušit rezervace, nastane dříve.</span><span class="sxs-lookup"><span data-stu-id="72d88-113">The application waits until the reservation date or until the customer decided to cancel the reservation, whichever comes first.</span></span>  
  
8.  <span data-ttu-id="72d88-114">Pokud zákazník zruší rezervace, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> kompenzace vlastní logiky spouští podle následujícího postupu:</span><span class="sxs-lookup"><span data-stu-id="72d88-114">If the customer cancels the reservation, the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> custom compensation logic runs according to the following logic:</span></span>  
  
    1.  <span data-ttu-id="72d88-115">Pokud zákazník má účet neprémiové a je menší než 10 dní před datem rezervace, pak je stále účtovat poplatek služby; aplikace, jinak hodnota náhrad poplatek služby.</span><span class="sxs-lookup"><span data-stu-id="72d88-115">If the customer has a non-premium account and it is less than 10 days prior to the reservation date, then the service fee is still charged; otherwise, the application refunds the service fee.</span></span>  
  
    2.  <span data-ttu-id="72d88-116">Zbytek compensable aktivity (vůz pořadí + vůz pořadí poplatek) jsou spouštěny podle logiky kompenzace výchozí, což je odpovídajícím způsobem v obráceném pořadí spouštění.</span><span class="sxs-lookup"><span data-stu-id="72d88-116">The rest of the compensable activities (truck order + truck order fee) are run according to the default compensation logic, which is to compensate in reverse order of execution.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="72d88-117">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="72d88-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="72d88-118">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete CustomCompensation.sln řešení.</span><span class="sxs-lookup"><span data-stu-id="72d88-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomCompensation.sln solution.</span></span> <span data-ttu-id="72d88-119">Je umístěn v adresáři \WF\Basic\Compensation\CustomCompensation.</span><span class="sxs-lookup"><span data-stu-id="72d88-119">It is located in the \WF\Basic\Compensation\CustomCompensation directory.</span></span>  
  
2.  <span data-ttu-id="72d88-120">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="72d88-120">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="72d88-121">Stisknutím kombinace kláves CTRL + F5 a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="72d88-121">Press CTRL + F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="72d88-122">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="72d88-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="72d88-123">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="72d88-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="72d88-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="72d88-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="72d88-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="72d88-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`