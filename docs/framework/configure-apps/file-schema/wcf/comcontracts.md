---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919479"
---
# <a name="comcontracts"></a><span data-ttu-id="6c6d3-101">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="6c6d3-101">\<comContracts></span></span>
<span data-ttu-id="6c6d3-102">`comContracts` Konfigurační oddíl obsahuje prvky, které umožňují zadat různé vlastnosti smlouvy služby COM+ Integration Service.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-102">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="6c6d3-103">Zadání oboru názvů a kontraktu</span><span class="sxs-lookup"><span data-stu-id="6c6d3-103">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="6c6d3-104">Kontrakty integrační služby com+ jsou aktuálně omezeny `http://tempuri.org` na obor názvů a název kontraktu je odvozen z doprovodného rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-104">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="6c6d3-105">Můžete však zadat alternativy pomocí `comContracts` oddílu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-105">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="6c6d3-106">Pomocí následující konfigurace můžete například zadat obor názvů a název kontraktu služby a také možnost vyhodnotit využití u vazeb s relacemi.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-106">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="6c6d3-107">Po inicializaci služby se zadané obory názvů a názvy kontraktů aplikují na vygenerované popisy služby.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-107">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="6c6d3-108">Pokud je tato část prázdná, použije se pro inicializaci služby výchozí obor názvů a název kontraktu z doprovodného IDENTIFIKÁTORu rozhraní COM.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-108">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="6c6d3-109">Kromě toho můžete pomocí [ \<elementu prvků exposedMethod >](exposedmethod.md) určit metody com+, které jsou vystaveny v případě, že je rozhraní komponenty modelu COM vystaveno jako webová služba.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-109">In addition, you can use the [\<exposedMethod>](exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="6c6d3-110">[ \<> PersistableTypes](persistabletypes.md) můžete použít také k určení trvalých typů, které se používají v integraci.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-110">You can also use the [\<persistableTypes>](persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="6c6d3-111">Nakonec můžete pomocí [ \<elementu typu UserDefinedType >](userdefinedtype.md) zahrnout uživatelsky definované typy (UDT), které mají být zahrnuty do kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-111">Finally, you can use the [\<userDefinedType>](userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c6d3-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c6d3-112">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="6c6d3-113">\<Prvků exposedMethod ></span><span class="sxs-lookup"><span data-stu-id="6c6d3-113">\<exposedMethod></span></span>](exposedmethod.md)
- [<span data-ttu-id="6c6d3-114">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="6c6d3-114">\<persistableTypes></span></span>](persistabletypes.md)
- [<span data-ttu-id="6c6d3-115">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="6c6d3-115">\<userDefinedType></span></span>](userdefinedtype.md)
- [<span data-ttu-id="6c6d3-116">\<comContract></span><span class="sxs-lookup"><span data-stu-id="6c6d3-116">\<comContract></span></span>](comcontract.md)
- [<span data-ttu-id="6c6d3-117">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="6c6d3-117">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="6c6d3-118">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="6c6d3-118">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
