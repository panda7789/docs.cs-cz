---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: d1a48fa2ed90999a66f4c1f84b7cfaa9a0e79f6a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940583"
---
# <a name="userdefinedtype"></a><span data-ttu-id="35584-101">\<Typu UserDefinedType ></span><span class="sxs-lookup"><span data-stu-id="35584-101">\<userDefinedType></span></span>
<span data-ttu-id="35584-102">Představuje uživatelem definovaný typ (UDT), který má být zahrnut do kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="35584-102">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
 <span data-ttu-id="35584-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="35584-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="35584-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="35584-104">\<comContracts></span></span>  
<span data-ttu-id="35584-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="35584-105">\<comContract></span></span>  
<span data-ttu-id="35584-106">\<userDefinedTypes ></span><span class="sxs-lookup"><span data-stu-id="35584-106">\<userDefinedTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35584-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35584-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35584-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="35584-108">Attributes and Elements</span></span>  
 <span data-ttu-id="35584-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="35584-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35584-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="35584-110">Attributes</span></span>  
  
|<span data-ttu-id="35584-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="35584-111">Attribute</span></span>|<span data-ttu-id="35584-112">Popis</span><span class="sxs-lookup"><span data-stu-id="35584-112">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="35584-113">Volitelný atribut, který obsahuje řetězec, který poskytuje název čitelného typu.</span><span class="sxs-lookup"><span data-stu-id="35584-113">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="35584-114">Toto není používáno modulem runtime, ale pomáhá čtenářům odlišit typy.</span><span class="sxs-lookup"><span data-stu-id="35584-114">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="35584-115">Řetězec identifikátoru GUID, který identifikuje konkrétní typ UDT v registrované knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="35584-115">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="35584-116">Řetězec identifikátoru GUID identifikující knihovnu registrovaných typů, která definuje typ.</span><span class="sxs-lookup"><span data-stu-id="35584-116">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="35584-117">Řetězec, který určuje verzi knihovny typů, která definuje typ.</span><span class="sxs-lookup"><span data-stu-id="35584-117">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35584-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="35584-118">Child Elements</span></span>  
 <span data-ttu-id="35584-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="35584-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35584-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="35584-120">Parent Elements</span></span>  
  
|<span data-ttu-id="35584-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="35584-121">Element</span></span>|<span data-ttu-id="35584-122">Popis</span><span class="sxs-lookup"><span data-stu-id="35584-122">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="35584-123">Kolekce `userDefinedType` prvků.</span><span class="sxs-lookup"><span data-stu-id="35584-123">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35584-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35584-124">Remarks</span></span>  
 <span data-ttu-id="35584-125">Prostředí Integration runtime modelu COM+ vytvoří služby kontrolou knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="35584-125">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="35584-126">Pokud komponenta modelu COM+ obsahuje metody, které předávají VARIANTu, systém nemůže určit skutečné typy, které mají být předány před modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="35584-126">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="35584-127">Proto při pokusu o předání uživatelem definovaného typu (UDT) v rámci varianty se nezdaří, protože se nejedná o známý typ pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="35584-127">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="35584-128">Chcete-li tento problém obejít, můžete přidat UDT do konfiguračního souboru, aby je bylo možné zahrnout do příslušného kontraktu služby jako známé typy.</span><span class="sxs-lookup"><span data-stu-id="35584-128">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="35584-129">Aby to bylo možné, musíte jedinečně identifikovat UDT a kontrakty, tedy původní rozhraní COM, která je používá.</span><span class="sxs-lookup"><span data-stu-id="35584-129">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="35584-130">Následující příklad ukazuje přidání dvou specifických UDT do oddílu <`userDefinedTypes`> konfiguračního souboru pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="35584-130">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
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
  
 <span data-ttu-id="35584-131">Při inicializaci služby modul Integration runtime vyhledá zadané typy a přidá je do kolekce známých typů pro zadané kontrakty.</span><span class="sxs-lookup"><span data-stu-id="35584-131">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35584-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35584-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [<span data-ttu-id="35584-133">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="35584-133">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="35584-134">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="35584-134">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="35584-135">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="35584-135">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
