---
title: '&lt;comContract&gt;'
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: e2addbada7f55076ae919d93c897991a7ec0fcd8
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207963"
---
# <a name="ltcomcontractgt"></a><span data-ttu-id="b8a26-102">&lt;comContract&gt;</span><span class="sxs-lookup"><span data-stu-id="b8a26-102">&lt;comContract&gt;</span></span>
<span data-ttu-id="b8a26-103">Určuje kontrakt služby integrace modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="b8a26-103">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="b8a26-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8a26-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8a26-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="b8a26-105">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8a26-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8a26-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8a26-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b8a26-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b8a26-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b8a26-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8a26-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="b8a26-109">Attributes</span></span>  
  
|<span data-ttu-id="b8a26-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="b8a26-110">Attribute</span></span>|<span data-ttu-id="b8a26-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b8a26-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8a26-112">kontrakt</span><span class="sxs-lookup"><span data-stu-id="b8a26-112">contract</span></span>|<span data-ttu-id="b8a26-113">Řetězec, který obsahuje typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b8a26-113">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="b8a26-114">name</span><span class="sxs-lookup"><span data-stu-id="b8a26-114">name</span></span>|<span data-ttu-id="b8a26-115">Řetězec obsahující název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b8a26-115">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="b8a26-116">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="b8a26-116">namespace</span></span>|<span data-ttu-id="b8a26-117">Řetězec, který obsahuje obor názvů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b8a26-117">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="b8a26-118">Vlastnost requiresSession</span><span class="sxs-lookup"><span data-stu-id="b8a26-118">requiresSession</span></span>|<span data-ttu-id="b8a26-119">Logická hodnota, která určuje, zda lze kontrakt použít pouze vazby s relacemi.</span><span class="sxs-lookup"><span data-stu-id="b8a26-119">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="b8a26-120">Při inicializaci služby modulu runtime integrace zajišťuje, že toto nastavení je konzistentní s typem vazby který se má použít.</span><span class="sxs-lookup"><span data-stu-id="b8a26-120">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="b8a26-121">Je vygenerována výjimka, pokud jeden nebo více vazeb pro kontrakt je v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="b8a26-121">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="b8a26-122">Pokud je tato vlastnost `false`a je jednosměrná kanál používá a [parametry out] existuje, je vygenerována výjimka.</span><span class="sxs-lookup"><span data-stu-id="b8a26-122">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8a26-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b8a26-123">Child Elements</span></span>  
  
|<span data-ttu-id="b8a26-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="b8a26-124">Element</span></span>|<span data-ttu-id="b8a26-125">Popis</span><span class="sxs-lookup"><span data-stu-id="b8a26-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8a26-126">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="b8a26-126">persistableTypes</span></span>|<span data-ttu-id="b8a26-127">Všechny trvalé typy.</span><span class="sxs-lookup"><span data-stu-id="b8a26-127">All the persistable types.</span></span>|  
|<span data-ttu-id="b8a26-128">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="b8a26-128">userDefinedTypes</span></span>|<span data-ttu-id="b8a26-129">Kolekce z uživateli definované typy (UDT), který je součástí kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="b8a26-129">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="b8a26-130">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="b8a26-130">exposedMethods</span></span>|<span data-ttu-id="b8a26-131">Kolekce metod modelu COM +, které jsou vystaveny při vystavení rozhraní komponenty COM + jako webovou službu.</span><span class="sxs-lookup"><span data-stu-id="b8a26-131">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8a26-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b8a26-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b8a26-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="b8a26-133">Element</span></span>|<span data-ttu-id="b8a26-134">Popis</span><span class="sxs-lookup"><span data-stu-id="b8a26-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8a26-135">comContracts</span><span class="sxs-lookup"><span data-stu-id="b8a26-135">comContracts</span></span>|<span data-ttu-id="b8a26-136">Obsahuje kolekci `comContract` elementy.</span><span class="sxs-lookup"><span data-stu-id="b8a26-136">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8a26-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8a26-137">Remarks</span></span>  
 <span data-ttu-id="b8a26-138">Kontrakty služby integrace modelu COM + jsou momentálně omezené jenom na `http://tempuri.org` oboru názvů a název smlouvy je odvozen z rozhraní COM podpůrné.</span><span class="sxs-lookup"><span data-stu-id="b8a26-138">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="b8a26-139">Alternativy můžete však určit pomocí `comContracts` část, stejně jako `comContract` element v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b8a26-139">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="b8a26-140">Například můžete použít následující konfigurace k určení oboru názvů, název kontraktu a uživatelsky definované typy, které mají být zahrnuty, jakož i další nastavení pro kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="b8a26-140">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="b8a26-141">Při inicializaci služby zadaných oborů názvů trasy a názvy kontraktů se použijí na popis generované služeb.</span><span class="sxs-lookup"><span data-stu-id="b8a26-141">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a26-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8a26-142">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="b8a26-143">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="b8a26-143">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="b8a26-144">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="b8a26-144">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="b8a26-145">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="b8a26-145">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
