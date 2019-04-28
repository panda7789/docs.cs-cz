---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: 8694f83a731363f83cb09de43214eb4b211ef5ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704281"
---
# <a name="comcontract"></a><span data-ttu-id="1b0f3-101">\<comContract></span><span class="sxs-lookup"><span data-stu-id="1b0f3-101">\<comContract></span></span>
<span data-ttu-id="1b0f3-102">Určuje kontrakt služby integrace modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-102">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="1b0f3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1b0f3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1b0f3-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="1b0f3-104">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b0f3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b0f3-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b0f3-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1b0f3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1b0f3-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b0f3-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="1b0f3-108">Attributes</span></span>  
  
|<span data-ttu-id="1b0f3-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="1b0f3-109">Attribute</span></span>|<span data-ttu-id="1b0f3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="1b0f3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b0f3-111">kontrakt</span><span class="sxs-lookup"><span data-stu-id="1b0f3-111">contract</span></span>|<span data-ttu-id="1b0f3-112">Řetězec, který obsahuje typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-112">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="1b0f3-113">name</span><span class="sxs-lookup"><span data-stu-id="1b0f3-113">name</span></span>|<span data-ttu-id="1b0f3-114">Řetězec obsahující název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-114">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="1b0f3-115">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="1b0f3-115">namespace</span></span>|<span data-ttu-id="1b0f3-116">Řetězec, který obsahuje obor názvů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-116">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="1b0f3-117">Vlastnost requiresSession</span><span class="sxs-lookup"><span data-stu-id="1b0f3-117">requiresSession</span></span>|<span data-ttu-id="1b0f3-118">Logická hodnota, která určuje, zda lze kontrakt použít pouze vazby s relacemi.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-118">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="1b0f3-119">Při inicializaci služby modulu runtime integrace zajišťuje, že toto nastavení je konzistentní s typem vazby který se má použít.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-119">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="1b0f3-120">Je vygenerována výjimka, pokud jeden nebo více vazeb pro kontrakt je v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-120">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="1b0f3-121">Pokud je tato vlastnost `false`a je jednosměrná kanál používá a [parametry out] existuje, je vygenerována výjimka.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-121">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b0f3-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1b0f3-122">Child Elements</span></span>  
  
|<span data-ttu-id="1b0f3-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="1b0f3-123">Element</span></span>|<span data-ttu-id="1b0f3-124">Popis</span><span class="sxs-lookup"><span data-stu-id="1b0f3-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b0f3-125">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="1b0f3-125">persistableTypes</span></span>|<span data-ttu-id="1b0f3-126">Všechny trvalé typy.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-126">All the persistable types.</span></span>|  
|<span data-ttu-id="1b0f3-127">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="1b0f3-127">userDefinedTypes</span></span>|<span data-ttu-id="1b0f3-128">Kolekce z uživateli definované typy (UDT), který je součástí kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-128">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="1b0f3-129">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="1b0f3-129">exposedMethods</span></span>|<span data-ttu-id="1b0f3-130">Kolekce metod modelu COM +, které jsou vystaveny při vystavení rozhraní komponenty COM + jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-130">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b0f3-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1b0f3-131">Parent Elements</span></span>  
  
|<span data-ttu-id="1b0f3-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="1b0f3-132">Element</span></span>|<span data-ttu-id="1b0f3-133">Popis</span><span class="sxs-lookup"><span data-stu-id="1b0f3-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b0f3-134">comContracts</span><span class="sxs-lookup"><span data-stu-id="1b0f3-134">comContracts</span></span>|<span data-ttu-id="1b0f3-135">Obsahuje kolekci `comContract` elementy.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-135">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b0f3-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b0f3-136">Remarks</span></span>  
 <span data-ttu-id="1b0f3-137">Kontrakty služby integrace modelu COM + jsou momentálně omezené jenom na `http://tempuri.org` oboru názvů a název smlouvy je odvozen z rozhraní COM podpůrné.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-137">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="1b0f3-138">Alternativy můžete však určit pomocí `comContracts` část, stejně jako `comContract` element v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-138">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="1b0f3-139">Například můžete použít následující konfigurace k určení oboru názvů, název kontraktu a uživatelsky definované typy, které mají být zahrnuty, jakož i další nastavení pro kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-139">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="1b0f3-140">Při inicializaci služby zadaných oborů názvů trasy a názvy kontraktů se použijí na popis generované služeb.</span><span class="sxs-lookup"><span data-stu-id="1b0f3-140">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b0f3-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b0f3-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="1b0f3-142">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="1b0f3-142">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="1b0f3-143">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="1b0f3-143">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="1b0f3-144">Postupy: Konfigurace nastavení služby modelu COM +</span><span class="sxs-lookup"><span data-stu-id="1b0f3-144">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
