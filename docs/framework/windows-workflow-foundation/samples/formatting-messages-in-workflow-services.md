---
title: Formátování zpráv ve službách pracovních postupů
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eb9a6b3a83a28154dc968bd4c1c41d34028bdd41
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45590192"
---
# <a name="formatting-messages-in-workflow-services"></a><span data-ttu-id="c793d-102">Formátování zpráv ve službách pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c793d-102">Formatting messages in Workflow Services</span></span>
<span data-ttu-id="c793d-103">Tento příklad ukazuje, jak různé uživatelské typy mohou být použity v zasílání zpráv aktivity (WF služby).</span><span class="sxs-lookup"><span data-stu-id="c793d-103">This sample shows how different user types can be used in messaging activities (WF services).</span></span> <span data-ttu-id="c793d-104">Ukázka service je služba schválení jednoduché výdajů a zpřístupňuje tří operací.</span><span class="sxs-lookup"><span data-stu-id="c793d-104">The sample service is a simple expense approval service and exposes three operations.</span></span> <span data-ttu-id="c793d-105">`ApproveExpense` přijímá typ kontraktu dat a ukazuje způsob použití známých typů.</span><span class="sxs-lookup"><span data-stu-id="c793d-105">`ApproveExpense` takes a data contract type and shows how to use known types.</span></span> <span data-ttu-id="c793d-106">Operace vrátí `true` nebo `false` na základě doby, výdajů.</span><span class="sxs-lookup"><span data-stu-id="c793d-106">The operation returns `true` or `false` based on the expense amount.</span></span> <span data-ttu-id="c793d-107">`ApprovePO` Typ XmlSerializer, který přijímá a vrací `true` nebo `false` na základě doby, výdajů.`ApprovedVendor`</span><span class="sxs-lookup"><span data-stu-id="c793d-107">`ApprovePO` takes an XmlSerializer type and returns `true` or `false` based on the expense amount.`ApprovedVendor`</span></span> <span data-ttu-id="c793d-108">Typ kontraktu zprávy přijímá a vrací `true` nebo `false` Pokud dodavatel je v seznamu schválených dodavatelů nebo pokud žádost pochází z finančního oddělení (finančního oddělení můžete použít libovolného dodavatele).</span><span class="sxs-lookup"><span data-stu-id="c793d-108">takes a message contract type and returns `true` or `false` if the vendor is in the list of approved vendors or if the request came from the finance department (the finance department can use any vendor).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="c793d-109">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="c793d-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="c793d-110">Načítání řešení projektu v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="c793d-110">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="c793d-111">První spuštění služby, vygenerované v \FormatterService\bin\debug\ [základní adresář řešení]</span><span class="sxs-lookup"><span data-stu-id="c793d-111">First run the service, generated in [solution base directory]\FormatterService\bin\debug\\</span></span>  
  
3.  <span data-ttu-id="c793d-112">Za druhé spuštění klientské aplikace vygenerované v \FormatterClient\bin\debug [základní adresář řešení].</span><span class="sxs-lookup"><span data-stu-id="c793d-112">Second, run the Client application generated in [solution base directory]\FormatterClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="c793d-113">Klient volá tří typů operací ve službě a zobrazí výsledky.</span><span class="sxs-lookup"><span data-stu-id="c793d-113">The client calls three operations on the service and prints the results.</span></span> <span data-ttu-id="c793d-114">Jakmile budete hotovi, stisknutím klávesy ENTER ukončete klienta a pak službu.</span><span class="sxs-lookup"><span data-stu-id="c793d-114">When complete, press ENTER to exit the client and then the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c793d-115">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="c793d-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c793d-116">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c793d-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c793d-117">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c793d-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c793d-118">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c793d-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`