---
title: '&lt;userDefinedType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0baac8dc6a9899261a490a257dbae0e7eb4d2ced
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserdefinedtypegt"></a><span data-ttu-id="b992e-102">&lt;userDefinedType&gt;</span><span class="sxs-lookup"><span data-stu-id="b992e-102">&lt;userDefinedType&gt;</span></span>
<span data-ttu-id="b992e-103">Představuje uživatel definovaný typ (UDT), které má být součástí kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="b992e-103">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
 <span data-ttu-id="b992e-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b992e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b992e-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="b992e-105">\<comContracts></span></span>  
<span data-ttu-id="b992e-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="b992e-106">\<comContract></span></span>  
<span data-ttu-id="b992e-107">\<userDefinedTypes ></span><span class="sxs-lookup"><span data-stu-id="b992e-107">\<userDefinedTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b992e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b992e-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b992e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b992e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b992e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b992e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b992e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b992e-111">Attributes</span></span>  
  
|<span data-ttu-id="b992e-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b992e-112">Attribute</span></span>|<span data-ttu-id="b992e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b992e-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="b992e-114">Volitelný atribut, který obsahuje řetězec, který obsahuje název typu čitelné.</span><span class="sxs-lookup"><span data-stu-id="b992e-114">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="b992e-115">Tento není používán modulu runtime ale pomáhá čtečka čipových karet k rozlišení typy.</span><span class="sxs-lookup"><span data-stu-id="b992e-115">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="b992e-116">Identifikátor GUID řetězec, který určuje konkrétní typ UDT v knihovně registrovaného typu.</span><span class="sxs-lookup"><span data-stu-id="b992e-116">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="b992e-117">Identifikátor GUID řetězec, který identifikuje registrovaného typu knihovnu, která definuje typ.</span><span class="sxs-lookup"><span data-stu-id="b992e-117">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="b992e-118">Řetězec, který určuje typ knihovní verze, která definuje typ.</span><span class="sxs-lookup"><span data-stu-id="b992e-118">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b992e-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b992e-119">Child Elements</span></span>  
 <span data-ttu-id="b992e-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="b992e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b992e-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b992e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b992e-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="b992e-122">Element</span></span>|<span data-ttu-id="b992e-123">Popis</span><span class="sxs-lookup"><span data-stu-id="b992e-123">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="b992e-124">Kolekce `userDefinedType` elementy.</span><span class="sxs-lookup"><span data-stu-id="b992e-124">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b992e-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b992e-125">Remarks</span></span>  
 <span data-ttu-id="b992e-126">Modul runtime integrace COM + vytvoří služby zkontrolováním knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="b992e-126">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="b992e-127">Pokud komponentu modelu COM + obsahuje metody, které předat hodnotu typu VARIANT, systém nemůže určit skutečné typy, které mají být předána před runtime.</span><span class="sxs-lookup"><span data-stu-id="b992e-127">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="b992e-128">Proto při pokusu o předání uživatel definovaný typ (UDT) v rámci hodnotu typu VARIANT se nezdaří, protože není známý typ pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="b992e-128">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="b992e-129">Chcete-li tento problém obejít, můžete přidat UDT do konfiguračního souboru tak, aby mohly být zahrnuta jako známé typy na příslušnou službu kontrakt.</span><span class="sxs-lookup"><span data-stu-id="b992e-129">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="b992e-130">Chcete-li to provést, máte k jednoznačné identifikaci UDT a smluv, tedy původní COM alespoň jedno rozhraní používající ho.</span><span class="sxs-lookup"><span data-stu-id="b992e-130">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="b992e-131">Následující příklad ukazuje dva konkrétní UDT k přidání <`userDefinedTypes`> oddílu konfiguračního souboru pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="b992e-131">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <userDefinedTypes>  
         <userDefinedType name="CustomerType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">  
         </userDefinedType>  
         <userDefinedType name="AddressType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">  
         </userDefinedType>  
      </userDefinedTypes>  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="b992e-132">Při inicializaci služby runtime integrace vyhledá určené typy a přidá je do kolekce známé typy pro zadaný smlouvy.</span><span class="sxs-lookup"><span data-stu-id="b992e-132">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b992e-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="b992e-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>  
 <xref:System.ServiceModel.Configuration.ComUdtElementCollection>  
 <xref:System.ServiceModel.Configuration.ComUdtElement>  
 [<span data-ttu-id="b992e-134">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="b992e-134">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="b992e-135">Integrace s aplikacemi modelu COM +</span><span class="sxs-lookup"><span data-stu-id="b992e-135">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="b992e-136">Postupy: Konfigurace nastavení služby COM +</span><span class="sxs-lookup"><span data-stu-id="b992e-136">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
