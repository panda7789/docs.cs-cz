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
ms.openlocfilehash: fe6de09213c6f980e8eb205a318aae50033b2a84
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155229"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="8e301-102">Element \<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="8e301-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="8e301-103">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="8e301-103">Contains cryptography settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**

## <a name="syntax"></a><span data-ttu-id="8e301-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e301-104">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e301-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8e301-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8e301-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8e301-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e301-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="8e301-107">Attributes</span></span>  
 <span data-ttu-id="8e301-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="8e301-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e301-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8e301-109">Child Elements</span></span>  
  
|<span data-ttu-id="8e301-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="8e301-110">Element</span></span>|<span data-ttu-id="8e301-111">Description</span><span class="sxs-lookup"><span data-stu-id="8e301-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|<span data-ttu-id="8e301-112">Obsahuje mapování tříd na popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="8e301-112">Contains mappings of classes to friendly names.</span></span>|  
|[\<oidMap>](oidmap-element.md)|<span data-ttu-id="8e301-113">Obsahuje mapování identifikátoru objektu ASN. 1 na třídy.</span><span class="sxs-lookup"><span data-stu-id="8e301-113">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e301-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8e301-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8e301-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="8e301-115">Element</span></span>|<span data-ttu-id="8e301-116">Description</span><span class="sxs-lookup"><span data-stu-id="8e301-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8e301-117">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e301-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="8e301-118">Obsahuje `cryptographySettings` element.</span><span class="sxs-lookup"><span data-stu-id="8e301-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8e301-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e301-119">Example</span></span>  
 <span data-ttu-id="8e301-120">Následující příklad ukazuje, jak použít **\<cryptographySettings>** element k zahrnutí mapování názvů kryptografie a mapování OID.</span><span class="sxs-lookup"><span data-stu-id="8e301-120">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="8e301-121">Tento příklad nakonfiguruje modul runtime tak, že <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> vrátí `MyHashClass` objekt a `MyCryptoClass` Třída se mapuje na identifikátor objektu 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="8e301-121">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e301-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e301-122">See also</span></span>

- [<span data-ttu-id="8e301-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="8e301-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8e301-124">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="8e301-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8e301-125">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="8e301-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
