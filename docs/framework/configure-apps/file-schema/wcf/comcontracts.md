---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "69919479"
---
# \<comContracts>
<span data-ttu-id="53120-101">`comContracts`Konfigurační oddíl obsahuje prvky, které umožňují zadat různé vlastnosti smlouvy služby COM+ Integration Service.</span><span class="sxs-lookup"><span data-stu-id="53120-101">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="53120-102">Zadání oboru názvů a kontraktu</span><span class="sxs-lookup"><span data-stu-id="53120-102">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="53120-103">Kontrakty integrační služby COM+ jsou aktuálně omezeny na `http://tempuri.org` obor názvů a název kontraktu je odvozen z doprovodného rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="53120-103">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="53120-104">Můžete však zadat alternativy pomocí `comContracts` oddílu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="53120-104">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="53120-105">Pomocí následující konfigurace můžete například zadat obor názvů a název kontraktu služby a také možnost vyhodnotit využití u vazeb s relacemi.</span><span class="sxs-lookup"><span data-stu-id="53120-105">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="53120-106">Po inicializaci služby se zadané obory názvů a názvy kontraktů aplikují na vygenerované popisy služby.</span><span class="sxs-lookup"><span data-stu-id="53120-106">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="53120-107">Pokud je tato část prázdná, použije se pro inicializaci služby výchozí obor názvů a název kontraktu z doprovodného IDENTIFIKÁTORu rozhraní COM.</span><span class="sxs-lookup"><span data-stu-id="53120-107">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="53120-108">Kromě toho můžete použít [\<exposedMethod>](exposedmethod.md) element k určení metod modelu COM+, které jsou vystaveny v případě, že je rozhraní komponenty modelu COM vystaveno jako webová služba.</span><span class="sxs-lookup"><span data-stu-id="53120-108">In addition, you can use the [\<exposedMethod>](exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="53120-109">Můžete také použít [\<persistableTypes>](persistabletypes.md) k určení trvalých typů používaných v integraci.</span><span class="sxs-lookup"><span data-stu-id="53120-109">You can also use the [\<persistableTypes>](persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="53120-110">Nakonec můžete použít [\<userDefinedType>](userdefinedtype.md) element k zahrnutí uživatelsky definovaných typů (UDT), které mají být zahrnuty do kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="53120-110">Finally, you can use the [\<userDefinedType>](userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53120-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="53120-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [<span data-ttu-id="53120-112">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="53120-112">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="53120-113">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="53120-113">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
