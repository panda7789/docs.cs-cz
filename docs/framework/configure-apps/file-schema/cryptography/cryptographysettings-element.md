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
ms.openlocfilehash: 462db50a42e55c0c5a9570317ceeeb0ae69215a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927655"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="9d68e-102">\<cryptographySettings – element ></span><span class="sxs-lookup"><span data-stu-id="9d68e-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="9d68e-103">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="9d68e-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="9d68e-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9d68e-104">\<configuration></span></span>  
<span data-ttu-id="9d68e-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="9d68e-105">\<mscorlib></span></span>  
<span data-ttu-id="9d68e-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="9d68e-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d68e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d68e-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d68e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9d68e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9d68e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9d68e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d68e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="9d68e-110">Attributes</span></span>  
 <span data-ttu-id="9d68e-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="9d68e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d68e-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9d68e-112">Child Elements</span></span>  
  
|<span data-ttu-id="9d68e-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d68e-113">Element</span></span>|<span data-ttu-id="9d68e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9d68e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d68e-115">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="9d68e-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="9d68e-116">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="9d68e-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="9d68e-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="9d68e-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="9d68e-118">Obsahuje mapování identifikátoru objektu ASN. 1 na třídy.</span><span class="sxs-lookup"><span data-stu-id="9d68e-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d68e-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9d68e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9d68e-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d68e-120">Element</span></span>|<span data-ttu-id="9d68e-121">Popis</span><span class="sxs-lookup"><span data-stu-id="9d68e-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9d68e-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d68e-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="9d68e-123">`cryptographySettings` Obsahuje element.</span><span class="sxs-lookup"><span data-stu-id="9d68e-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9d68e-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d68e-124">Example</span></span>  
 <span data-ttu-id="9d68e-125">Následující příklad ukazuje, jak použít  **\<element cryptographySettings >** k zahrnutí mapování názvů kryptografie a mapování OID.</span><span class="sxs-lookup"><span data-stu-id="9d68e-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="9d68e-126">Tento příklad nakonfiguruje modul runtime tak <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> , že `MyHashClass` vrátí objekt a `MyCryptoClass` třída se mapuje na identifikátor objektu 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="9d68e-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d68e-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d68e-127">See also</span></span>

- [<span data-ttu-id="9d68e-128">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9d68e-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9d68e-129">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="9d68e-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9d68e-130">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="9d68e-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
