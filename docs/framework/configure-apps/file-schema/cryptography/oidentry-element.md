---
title: Element <oidEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: b1dc4c788576fd3cab55db5255617cc55e68594b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259056"
---
# <a name="oidentry-element"></a><span data-ttu-id="8c79a-102">\<oidentry – > – Element</span><span class="sxs-lookup"><span data-stu-id="8c79a-102">\<oidEntry> Element</span></span>
<span data-ttu-id="8c79a-103">Identifikátor objektu (OID) ASN.1 se mapuje na popisný název.</span><span class="sxs-lookup"><span data-stu-id="8c79a-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="8c79a-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="8c79a-104">\<configuration></span></span>  
<span data-ttu-id="8c79a-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="8c79a-105">\<mscorlib></span></span>  
<span data-ttu-id="8c79a-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="8c79a-106">\<cryptographySettings></span></span>  
<span data-ttu-id="8c79a-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="8c79a-107">\<oidMap></span></span>  
<span data-ttu-id="8c79a-108">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="8c79a-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c79a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c79a-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c79a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8c79a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8c79a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8c79a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c79a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="8c79a-112">Attributes</span></span>  
  
|<span data-ttu-id="8c79a-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="8c79a-113">Attribute</span></span>|<span data-ttu-id="8c79a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8c79a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c79a-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="8c79a-115">**OID**</span></span>|<span data-ttu-id="8c79a-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8c79a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="8c79a-117">Určuje Identifikátor ASN.1 odpovídající algoritmus implementovaný pomocí vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="8c79a-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="8c79a-118">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="8c79a-118">**name**</span></span>|<span data-ttu-id="8c79a-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8c79a-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="8c79a-120">Určuje hodnotu **název** atribut [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) značky.</span><span class="sxs-lookup"><span data-stu-id="8c79a-120">Specifies the value for the **name** attribute in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c79a-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8c79a-121">Child Elements</span></span>  
 <span data-ttu-id="8c79a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="8c79a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c79a-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8c79a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8c79a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c79a-124">Element</span></span>|<span data-ttu-id="8c79a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="8c79a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8c79a-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c79a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="8c79a-127">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="8c79a-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="8c79a-128">Obsahuje `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="8c79a-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="8c79a-129">Obsahuje ASN.1 objekt identifikátor (OID), mapování na třídy.</span><span class="sxs-lookup"><span data-stu-id="8c79a-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c79a-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c79a-130">Remarks</span></span>  
 <span data-ttu-id="8c79a-131">Identifikátory objektů ASN.1 identifikovat v některé formáty kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="8c79a-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="8c79a-132">Mapování identifikátorů objektů na popisné názvy algoritmů, které chcete identifikovat.</span><span class="sxs-lookup"><span data-stu-id="8c79a-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c79a-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c79a-133">Example</span></span>  
 <span data-ttu-id="8c79a-134">Následující příklad ukazuje způsob použití  **\<oidentry – >** element namapovat identifikátor objektu pro algoritmus hash RIPEMD 160 implementace algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="8c79a-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c79a-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c79a-135">See also</span></span>
- [<span data-ttu-id="8c79a-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="8c79a-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="8c79a-137">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="8c79a-137">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="8c79a-138">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="8c79a-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="8c79a-139">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="8c79a-139">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="8c79a-140">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="8c79a-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
