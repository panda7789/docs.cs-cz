---
title: "Formátování zprávy v služeb pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ddbe0c4e1b4af422925c42044136396e4036469e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="formatting-messages-in-workflow-services"></a><span data-ttu-id="68d70-102">Formátování zprávy v služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="68d70-102">Formatting messages in Workflow Services</span></span>
<span data-ttu-id="68d70-103">Tento příklad ukazuje, jak jiného uživatele je možné použít typy v zasílání zpráv aktivity (WF služby).</span><span class="sxs-lookup"><span data-stu-id="68d70-103">This sample shows how different user types can be used in messaging activities (WF services).</span></span> <span data-ttu-id="68d70-104">Ukázka služby je služba schválení jednoduché náklady a zveřejňuje tří typů operací.</span><span class="sxs-lookup"><span data-stu-id="68d70-104">The sample service is a simple expense approval service and exposes three operations.</span></span> <span data-ttu-id="68d70-105">`ApproveExpense`datový typ smlouvy trvá a ukazuje, jak používat známé typy.</span><span class="sxs-lookup"><span data-stu-id="68d70-105">`ApproveExpense` takes a data contract type and shows how to use known types.</span></span> <span data-ttu-id="68d70-106">Vrátí operaci `true` nebo `false` založenou na velikosti náklady.</span><span class="sxs-lookup"><span data-stu-id="68d70-106">The operation returns `true` or `false` based on the expense amount.</span></span> <span data-ttu-id="68d70-107">`ApprovePO`Typ třídy XmlSerializer provede a vrátí `true` nebo `false` založenou na velikosti náklady.`ApprovedVendor`</span><span class="sxs-lookup"><span data-stu-id="68d70-107">`ApprovePO` takes an XmlSerializer type and returns `true` or `false` based on the expense amount.`ApprovedVendor`</span></span> <span data-ttu-id="68d70-108">načte typ kontrakt zprávy a vrátí `true` nebo `false` dodavatele je v seznamu schválených dodavatelů nebo pokud požadavek pochází z finančního oddělení (finančního oddělení můžete použít jakéhokoli dodavatele).</span><span class="sxs-lookup"><span data-stu-id="68d70-108">takes a message contract type and returns `true` or `false` if the vendor is in the list of approved vendors or if the request came from the finance department (the finance department can use any vendor).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="68d70-109">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="68d70-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="68d70-110">Načtení projektu řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="68d70-110">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="68d70-111">Nejprve spusťte službu, vygenerovaných \FormatterService\bin\debug\ [základní adresář řešení]</span><span class="sxs-lookup"><span data-stu-id="68d70-111">First run the service, generated in [solution base directory]\FormatterService\bin\debug\\</span></span>  
  
3.  <span data-ttu-id="68d70-112">Druhý spusťte klientskou aplikaci vygenerovaných \FormatterClient\bin\debug [základní adresář řešení].</span><span class="sxs-lookup"><span data-stu-id="68d70-112">Second, run the Client application generated in [solution base directory]\FormatterClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="68d70-113">Klient zavolá tří typů operací ve službě a zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="68d70-113">The client calls three operations on the service and prints the results.</span></span> <span data-ttu-id="68d70-114">Po dokončení stiskněte klávesu ENTER ukončíte klienta a pak službu.</span><span class="sxs-lookup"><span data-stu-id="68d70-114">When complete, press ENTER to exit the client and then the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68d70-115">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="68d70-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="68d70-116">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="68d70-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="68d70-117">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="68d70-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="68d70-118">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="68d70-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`  
  
## <a name="see-also"></a><span data-ttu-id="68d70-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="68d70-119">See Also</span></span>
