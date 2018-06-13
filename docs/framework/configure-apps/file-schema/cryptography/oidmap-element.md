---
title: '&lt;oidmap –&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: db39d7de3566647b5171b71940c78a9a0ab6f5f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350219"
---
# <a name="ltoidmapgt-element"></a><span data-ttu-id="fe59a-102">&lt;oidmap –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="fe59a-102">&lt;oidMap&gt; Element</span></span>
<span data-ttu-id="fe59a-103">Obsahuje ASN.1 objektu (OID) identifikátor mapování třídy.</span><span class="sxs-lookup"><span data-stu-id="fe59a-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="fe59a-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fe59a-104">\<configuration></span></span>  
<span data-ttu-id="fe59a-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="fe59a-105">\<mscorlib></span></span>  
<span data-ttu-id="fe59a-106">\<cryptographySettings – ></span><span class="sxs-lookup"><span data-stu-id="fe59a-106">\<cryptographySettings></span></span>  
<span data-ttu-id="fe59a-107">\<oidmap – ></span><span class="sxs-lookup"><span data-stu-id="fe59a-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe59a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe59a-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe59a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fe59a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fe59a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fe59a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe59a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="fe59a-111">Attributes</span></span>  
 <span data-ttu-id="fe59a-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="fe59a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe59a-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fe59a-113">Child Elements</span></span>  
  
|<span data-ttu-id="fe59a-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe59a-114">Element</span></span>|<span data-ttu-id="fe59a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="fe59a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe59a-116">\<oidentry – ></span><span class="sxs-lookup"><span data-stu-id="fe59a-116">\<oidEntry></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="fe59a-117">Mapuje identifikátor OID ASN.1 popisný název.</span><span class="sxs-lookup"><span data-stu-id="fe59a-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe59a-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fe59a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fe59a-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe59a-119">Element</span></span>|<span data-ttu-id="fe59a-120">Popis</span><span class="sxs-lookup"><span data-stu-id="fe59a-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fe59a-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe59a-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="fe59a-122">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="fe59a-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="fe59a-123">Obsahuje `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="fe59a-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fe59a-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe59a-124">Example</span></span>  
 <span data-ttu-id="fe59a-125">Následující příklad ukazuje, jak používat  **\<oidmap – >** element tak, aby obsahovala mapování identifikátor OID pro algoritmus hash RIPEMD-160 k implementaci pro tento algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="fe59a-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe59a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe59a-126">See Also</span></span>  
 [<span data-ttu-id="fe59a-127">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="fe59a-127">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="fe59a-128">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="fe59a-128">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="fe59a-129">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="fe59a-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="fe59a-130">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="fe59a-130">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="fe59a-131">Mapování identifikátorů objektů na algoritmy šifrování</span><span class="sxs-lookup"><span data-stu-id="fe59a-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
