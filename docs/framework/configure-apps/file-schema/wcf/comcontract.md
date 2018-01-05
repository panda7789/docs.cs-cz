---
title: '&lt;comContract&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fa70ba3cf8e66411812b84821e80772c9930f7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcomcontractgt"></a><span data-ttu-id="aaf78-102">&lt;comContract&gt;</span><span class="sxs-lookup"><span data-stu-id="aaf78-102">&lt;comContract&gt;</span></span>
<span data-ttu-id="aaf78-103">Určuje modelu COM + integrace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="aaf78-103">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="aaf78-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="aaf78-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="aaf78-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="aaf78-105">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf78-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaf78-106">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="string"  
      namespace="string"  
      name="string"  
      requireSession="Boolean">  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aaf78-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aaf78-107">Attributes and Elements</span></span>  
 <span data-ttu-id="aaf78-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aaf78-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aaf78-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="aaf78-109">Attributes</span></span>  
  
|<span data-ttu-id="aaf78-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="aaf78-110">Attribute</span></span>|<span data-ttu-id="aaf78-111">Popis</span><span class="sxs-lookup"><span data-stu-id="aaf78-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aaf78-112">kontrakt</span><span class="sxs-lookup"><span data-stu-id="aaf78-112">contract</span></span>|<span data-ttu-id="aaf78-113">Řetězec, který obsahuje typ smlouvy.</span><span class="sxs-lookup"><span data-stu-id="aaf78-113">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="aaf78-114">name</span><span class="sxs-lookup"><span data-stu-id="aaf78-114">name</span></span>|<span data-ttu-id="aaf78-115">Řetězec, který obsahuje název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="aaf78-115">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="aaf78-116">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="aaf78-116">namespace</span></span>|<span data-ttu-id="aaf78-117">Řetězec, který obsahuje obor názvů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="aaf78-117">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="aaf78-118">Vlastnost requiresSession</span><span class="sxs-lookup"><span data-stu-id="aaf78-118">requiresSession</span></span>|<span data-ttu-id="aaf78-119">Logická hodnota, která určuje, zda kontrakt lze použít pouze na relacemi vazby.</span><span class="sxs-lookup"><span data-stu-id="aaf78-119">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="aaf78-120">Při inicializaci služby modulu runtime integrace zajistí, že toto nastavení bude konzistentní s typ vazby, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="aaf78-120">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="aaf78-121">Výjimku se vygeneruje, pokud jeden nebo více vazby pro daný kontrakt je v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="aaf78-121">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="aaf78-122">Pokud je tato vlastnost `false`a jednosměrné kanál, který je používán a [parametry out] existují, generuje se taky výjimku.</span><span class="sxs-lookup"><span data-stu-id="aaf78-122">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aaf78-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aaf78-123">Child Elements</span></span>  
  
|<span data-ttu-id="aaf78-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="aaf78-124">Element</span></span>|<span data-ttu-id="aaf78-125">Popis</span><span class="sxs-lookup"><span data-stu-id="aaf78-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aaf78-126">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="aaf78-126">persistableTypes</span></span>|<span data-ttu-id="aaf78-127">Všechny trvalá typy.</span><span class="sxs-lookup"><span data-stu-id="aaf78-127">All the persistable types.</span></span>|  
|<span data-ttu-id="aaf78-128">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="aaf78-128">userDefinedTypes</span></span>|<span data-ttu-id="aaf78-129">Kolekce z uživatele definované typy (UDT), které má být součástí kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="aaf78-129">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="aaf78-130">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="aaf78-130">exposedMethods</span></span>|<span data-ttu-id="aaf78-131">Kolekce metod modelu COM +, které jsou zveřejněné, pokud je jako webovou službu vystavený rozhraní komponenty modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="aaf78-131">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aaf78-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aaf78-132">Parent Elements</span></span>  
  
|<span data-ttu-id="aaf78-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="aaf78-133">Element</span></span>|<span data-ttu-id="aaf78-134">Popis</span><span class="sxs-lookup"><span data-stu-id="aaf78-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aaf78-135">comContracts</span><span class="sxs-lookup"><span data-stu-id="aaf78-135">comContracts</span></span>|<span data-ttu-id="aaf78-136">Obsahuje kolekci `comContract` elementy.</span><span class="sxs-lookup"><span data-stu-id="aaf78-136">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaf78-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aaf78-137">Remarks</span></span>  
 <span data-ttu-id="aaf78-138">Kontrakty služeb integrace COM + jsou aktuálně omezeno na obor názvů "http://tempuri.org" a název smlouvy je odvozený od podpůrné rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="aaf78-138">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="aaf78-139">Můžete však zadat alternativy pomocí `comContracts` části, a taky `comContract` element v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="aaf78-139">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="aaf78-140">Například můžete použít následující konfigurace a zadat obor názvů, název kontraktu a uživatelem definované typy, které mají být zahrnuty, jakož i další nastavení pro kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="aaf78-140">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="aaf78-141">Při inicializaci služby zadaných oborů názvů a názvy kontraktu platí pro popis generovaného služby.</span><span class="sxs-lookup"><span data-stu-id="aaf78-141">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaf78-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="aaf78-142">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="aaf78-143">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="aaf78-143">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="aaf78-144">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="aaf78-144">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="aaf78-145">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="aaf78-145">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
