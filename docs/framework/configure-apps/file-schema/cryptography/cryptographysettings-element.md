---
title: Element <cryptographySettings>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: ec3a5a73caa901a21e22dbec7500af9153e01ef4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164135"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="9de1b-102">\<cryptographySettings – > – Element</span><span class="sxs-lookup"><span data-stu-id="9de1b-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="9de1b-103">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="9de1b-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="9de1b-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="9de1b-104">\<configuration></span></span>  
<span data-ttu-id="9de1b-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="9de1b-105">\<mscorlib></span></span>  
<span data-ttu-id="9de1b-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="9de1b-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9de1b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9de1b-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9de1b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9de1b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9de1b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9de1b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9de1b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="9de1b-110">Attributes</span></span>  
 <span data-ttu-id="9de1b-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="9de1b-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9de1b-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9de1b-112">Child Elements</span></span>  
  
|<span data-ttu-id="9de1b-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="9de1b-113">Element</span></span>|<span data-ttu-id="9de1b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9de1b-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9de1b-115">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="9de1b-115">\<cryptoNameMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="9de1b-116">Obsahuje mapování tříd pro popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="9de1b-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="9de1b-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="9de1b-117">\<oidMap></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="9de1b-118">Obsahuje ASN.1 objekt identifikátor (OID), mapování na třídy.</span><span class="sxs-lookup"><span data-stu-id="9de1b-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9de1b-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9de1b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9de1b-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="9de1b-120">Element</span></span>|<span data-ttu-id="9de1b-121">Popis</span><span class="sxs-lookup"><span data-stu-id="9de1b-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9de1b-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9de1b-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="9de1b-123">Obsahuje `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="9de1b-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9de1b-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="9de1b-124">Example</span></span>  
 <span data-ttu-id="9de1b-125">Následující příklad ukazuje způsob použití  **\<cryptographySettings – >** element tak, aby obsahovala OID mapování a mapování názvů kryptografie.</span><span class="sxs-lookup"><span data-stu-id="9de1b-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="9de1b-126">Tento příklad konfiguruje modul runtime tak, aby <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> vrátí `MyHashClass` objektu a `MyCryptoClass` třídy mapuje 1.3.36.2.1 identifikátor objektu.</span><span class="sxs-lookup"><span data-stu-id="9de1b-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9de1b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9de1b-127">See also</span></span>

- [<span data-ttu-id="9de1b-128">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9de1b-128">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="9de1b-129">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="9de1b-129">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="9de1b-130">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="9de1b-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
