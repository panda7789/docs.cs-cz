---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850025"
---
# \<comContract>
<span data-ttu-id="864e5-101">Určuje kontrakt služby integrace modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="864e5-101">Specifies a COM+ integration service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
## <a name="syntax"></a><span data-ttu-id="864e5-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="864e5-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="864e5-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="864e5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="864e5-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="864e5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="864e5-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="864e5-105">Attributes</span></span>  
  
|<span data-ttu-id="864e5-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="864e5-106">Attribute</span></span>|<span data-ttu-id="864e5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="864e5-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="864e5-108">dodavatele</span><span class="sxs-lookup"><span data-stu-id="864e5-108">contract</span></span>|<span data-ttu-id="864e5-109">Řetězec, který obsahuje typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="864e5-109">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="864e5-110">name</span><span class="sxs-lookup"><span data-stu-id="864e5-110">name</span></span>|<span data-ttu-id="864e5-111">Řetězec, který obsahuje název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="864e5-111">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="864e5-112">namespace</span><span class="sxs-lookup"><span data-stu-id="864e5-112">namespace</span></span>|<span data-ttu-id="864e5-113">Řetězec, který obsahuje obor názvů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="864e5-113">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="864e5-114">requiresSession</span><span class="sxs-lookup"><span data-stu-id="864e5-114">requiresSession</span></span>|<span data-ttu-id="864e5-115">Logická hodnota určující, zda lze kontrakt použít pouze pro vazby s relacemi.</span><span class="sxs-lookup"><span data-stu-id="864e5-115">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="864e5-116">Po inicializaci služby Integration runtime zajistí, že toto nastavení je konzistentní s typem vazby, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="864e5-116">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="864e5-117">Výjimka je vygenerována v případě, že jedna nebo více vazeb pro kontrakt jsou v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="864e5-117">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="864e5-118">Pokud je tato vlastnost `false` a používá se jednosměrný kanál a existují parametry [out], vygeneruje se taky výjimka.</span><span class="sxs-lookup"><span data-stu-id="864e5-118">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="864e5-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="864e5-119">Child Elements</span></span>  
  
|<span data-ttu-id="864e5-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="864e5-120">Element</span></span>|<span data-ttu-id="864e5-121">Description</span><span class="sxs-lookup"><span data-stu-id="864e5-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="864e5-122">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="864e5-122">persistableTypes</span></span>|<span data-ttu-id="864e5-123">Všechny typy, které jsou trvalé.</span><span class="sxs-lookup"><span data-stu-id="864e5-123">All the persistable types.</span></span>|  
|<span data-ttu-id="864e5-124">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="864e5-124">userDefinedTypes</span></span>|<span data-ttu-id="864e5-125">Kolekce uživatelsky definovaných typů (UDT), které mají být zahrnuty do kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="864e5-125">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="864e5-126">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="864e5-126">exposedMethods</span></span>|<span data-ttu-id="864e5-127">Kolekce metod modelu COM+, která je vystavena v případě, že je rozhraní součásti modelu COM vystaveno jako webová služba.</span><span class="sxs-lookup"><span data-stu-id="864e5-127">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="864e5-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="864e5-128">Parent Elements</span></span>  
  
|<span data-ttu-id="864e5-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="864e5-129">Element</span></span>|<span data-ttu-id="864e5-130">Description</span><span class="sxs-lookup"><span data-stu-id="864e5-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="864e5-131">comContracts</span><span class="sxs-lookup"><span data-stu-id="864e5-131">comContracts</span></span>|<span data-ttu-id="864e5-132">Obsahuje kolekci `comContract` prvků.</span><span class="sxs-lookup"><span data-stu-id="864e5-132">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="864e5-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="864e5-133">Remarks</span></span>  
 <span data-ttu-id="864e5-134">Kontrakty integrační služby COM+ jsou aktuálně omezeny na `http://tempuri.org` obor názvů a název kontraktu je odvozen z doprovodného rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="864e5-134">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="864e5-135">Můžete však zadat alternativy pomocí `comContracts` oddílu a také `comContract` elementu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="864e5-135">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="864e5-136">Pomocí následující konfigurace můžete například zadat obor názvů, název kontraktu a uživatelsky definované typy, které se mají zahrnout, a další nastavení pro kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="864e5-136">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="864e5-137">Po inicializaci služby se zadané obory názvů a názvy kontraktů aplikují na vygenerované popisy služby.</span><span class="sxs-lookup"><span data-stu-id="864e5-137">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="864e5-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="864e5-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="864e5-139">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="864e5-139">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="864e5-140">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="864e5-140">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
