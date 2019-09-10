---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850025"
---
# <a name="comcontract"></a><span data-ttu-id="429b3-101">\<comContract></span><span class="sxs-lookup"><span data-stu-id="429b3-101">\<comContract></span></span>
<span data-ttu-id="429b3-102">Určuje kontrakt služby integrace modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="429b3-102">Specifies a COM+ integration service contract.</span></span>  
  
<span data-ttu-id="429b3-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="429b3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="429b3-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="429b3-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="429b3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Konfigurační oddíl comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="429b3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="429b3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<comContract >**</span><span class="sxs-lookup"><span data-stu-id="429b3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="429b3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="429b3-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="429b3-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="429b3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="429b3-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="429b3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="429b3-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="429b3-110">Attributes</span></span>  
  
|<span data-ttu-id="429b3-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="429b3-111">Attribute</span></span>|<span data-ttu-id="429b3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="429b3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="429b3-113">Dodavatele</span><span class="sxs-lookup"><span data-stu-id="429b3-113">contract</span></span>|<span data-ttu-id="429b3-114">Řetězec, který obsahuje typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="429b3-114">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="429b3-115">name</span><span class="sxs-lookup"><span data-stu-id="429b3-115">name</span></span>|<span data-ttu-id="429b3-116">Řetězec, který obsahuje název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="429b3-116">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="429b3-117">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="429b3-117">namespace</span></span>|<span data-ttu-id="429b3-118">Řetězec, který obsahuje obor názvů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="429b3-118">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="429b3-119">requiresSession</span><span class="sxs-lookup"><span data-stu-id="429b3-119">requiresSession</span></span>|<span data-ttu-id="429b3-120">Logická hodnota určující, zda lze kontrakt použít pouze pro vazby s relacemi.</span><span class="sxs-lookup"><span data-stu-id="429b3-120">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="429b3-121">Po inicializaci služby Integration runtime zajistí, že toto nastavení je konzistentní s typem vazby, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="429b3-121">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="429b3-122">Výjimka je vygenerována v případě, že jedna nebo více vazeb pro kontrakt jsou v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="429b3-122">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="429b3-123">Pokud je `false`Tato vlastnost a používá se jednosměrný kanál a existují parametry [out], vygeneruje se taky výjimka.</span><span class="sxs-lookup"><span data-stu-id="429b3-123">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="429b3-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="429b3-124">Child Elements</span></span>  
  
|<span data-ttu-id="429b3-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="429b3-125">Element</span></span>|<span data-ttu-id="429b3-126">Popis</span><span class="sxs-lookup"><span data-stu-id="429b3-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="429b3-127">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="429b3-127">persistableTypes</span></span>|<span data-ttu-id="429b3-128">Všechny typy, které jsou trvalé.</span><span class="sxs-lookup"><span data-stu-id="429b3-128">All the persistable types.</span></span>|  
|<span data-ttu-id="429b3-129">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="429b3-129">userDefinedTypes</span></span>|<span data-ttu-id="429b3-130">Kolekce uživatelsky definovaných typů (UDT), které mají být zahrnuty do kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="429b3-130">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="429b3-131">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="429b3-131">exposedMethods</span></span>|<span data-ttu-id="429b3-132">Kolekce metod modelu COM+, která je vystavena v případě, že je rozhraní součásti modelu COM vystaveno jako webová služba.</span><span class="sxs-lookup"><span data-stu-id="429b3-132">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="429b3-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="429b3-133">Parent Elements</span></span>  
  
|<span data-ttu-id="429b3-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="429b3-134">Element</span></span>|<span data-ttu-id="429b3-135">Popis</span><span class="sxs-lookup"><span data-stu-id="429b3-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="429b3-136">comContracts</span><span class="sxs-lookup"><span data-stu-id="429b3-136">comContracts</span></span>|<span data-ttu-id="429b3-137">Obsahuje kolekci `comContract` prvků.</span><span class="sxs-lookup"><span data-stu-id="429b3-137">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="429b3-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="429b3-138">Remarks</span></span>  
 <span data-ttu-id="429b3-139">Kontrakty integrační služby com+ jsou aktuálně omezeny `http://tempuri.org` na obor názvů a název kontraktu je odvozen z doprovodného rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="429b3-139">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="429b3-140">Můžete však zadat alternativy pomocí `comContracts` oddílu a také `comContract` elementu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="429b3-140">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="429b3-141">Pomocí následující konfigurace můžete například zadat obor názvů, název kontraktu a uživatelsky definované typy, které se mají zahrnout, a další nastavení pro kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="429b3-141">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
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
  
 <span data-ttu-id="429b3-142">Po inicializaci služby se zadané obory názvů a názvy kontraktů aplikují na vygenerované popisy služby.</span><span class="sxs-lookup"><span data-stu-id="429b3-142">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="429b3-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="429b3-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="429b3-144">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="429b3-144">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="429b3-145">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="429b3-145">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="429b3-146">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="429b3-146">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
