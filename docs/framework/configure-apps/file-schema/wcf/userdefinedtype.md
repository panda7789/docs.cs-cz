---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 7a76e5a90fe3218bc0302501b71daa9de0b098bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854843"
---
# \<userDefinedType>
<span data-ttu-id="11b91-101">Představuje uživatelem definovaný typ (UDT), který má být zahrnut do kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="11b91-101">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<userDefinedTypes>**](userdefinedtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userDefinedType>**  
  
## <a name="syntax"></a><span data-ttu-id="11b91-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11b91-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11b91-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11b91-103">Attributes and Elements</span></span>  
 <span data-ttu-id="11b91-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11b91-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11b91-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="11b91-105">Attributes</span></span>  
  
|<span data-ttu-id="11b91-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="11b91-106">Attribute</span></span>|<span data-ttu-id="11b91-107">Popis</span><span class="sxs-lookup"><span data-stu-id="11b91-107">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="11b91-108">Volitelný atribut, který obsahuje řetězec, který poskytuje název čitelného typu.</span><span class="sxs-lookup"><span data-stu-id="11b91-108">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="11b91-109">Toto není používáno modulem runtime, ale pomáhá čtenářům odlišit typy.</span><span class="sxs-lookup"><span data-stu-id="11b91-109">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="11b91-110">Řetězec identifikátoru GUID, který identifikuje konkrétní typ UDT v registrované knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="11b91-110">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="11b91-111">Řetězec identifikátoru GUID identifikující knihovnu registrovaných typů, která definuje typ.</span><span class="sxs-lookup"><span data-stu-id="11b91-111">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="11b91-112">Řetězec, který určuje verzi knihovny typů, která definuje typ.</span><span class="sxs-lookup"><span data-stu-id="11b91-112">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11b91-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11b91-113">Child Elements</span></span>  
 <span data-ttu-id="11b91-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="11b91-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11b91-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11b91-115">Parent Elements</span></span>  
  
|<span data-ttu-id="11b91-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="11b91-116">Element</span></span>|<span data-ttu-id="11b91-117">Description</span><span class="sxs-lookup"><span data-stu-id="11b91-117">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="11b91-118">Kolekce `userDefinedType` prvků.</span><span class="sxs-lookup"><span data-stu-id="11b91-118">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11b91-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11b91-119">Remarks</span></span>  
 <span data-ttu-id="11b91-120">Prostředí Integration runtime modelu COM+ vytvoří služby kontrolou knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="11b91-120">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="11b91-121">Pokud komponenta modelu COM+ obsahuje metody, které předávají VARIANTu, systém nemůže určit skutečné typy, které mají být předány před modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="11b91-121">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="11b91-122">Proto při pokusu o předání uživatelem definovaného typu (UDT) v rámci varianty se nezdaří, protože se nejedná o známý typ pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="11b91-122">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="11b91-123">Chcete-li tento problém obejít, můžete přidat UDT do konfiguračního souboru, aby je bylo možné zahrnout do příslušného kontraktu služby jako známé typy.</span><span class="sxs-lookup"><span data-stu-id="11b91-123">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="11b91-124">Aby to bylo možné, musíte jedinečně identifikovat UDT a kontrakty, tedy původní rozhraní COM, která je používá.</span><span class="sxs-lookup"><span data-stu-id="11b91-124">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="11b91-125">Následující příklad ukazuje přidání dvou specifických UDT do `userDefinedTypes` oddílu <> konfiguračního souboru pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="11b91-125">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
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
  
 <span data-ttu-id="11b91-126">Při inicializaci služby modul Integration runtime vyhledá zadané typy a přidá je do kolekce známých typů pro zadané kontrakty.</span><span class="sxs-lookup"><span data-stu-id="11b91-126">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b91-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="11b91-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="11b91-128">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="11b91-128">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="11b91-129">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="11b91-129">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
