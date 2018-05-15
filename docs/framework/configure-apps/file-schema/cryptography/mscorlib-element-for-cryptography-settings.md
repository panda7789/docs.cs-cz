---
title: '&lt;mscorlib&gt; Element pro nastavení kryptografie'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 292937000eb1baca191c0960e8e496a128ee4696
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a><span data-ttu-id="b94b1-102">&lt;mscorlib&gt; Element pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="b94b1-102">&lt;mscorlib&gt; Element for Cryptography Settings</span></span>
<span data-ttu-id="b94b1-103">Obsahuje [ \<cryptographySettings – > element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="b94b1-103">Contains the [\<cryptographySettings> element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="b94b1-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="b94b1-104">\<configuration></span></span>  
<span data-ttu-id="b94b1-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="b94b1-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b94b1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b94b1-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b94b1-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b94b1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b94b1-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b94b1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b94b1-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="b94b1-109">Attributes</span></span>  
 <span data-ttu-id="b94b1-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="b94b1-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b94b1-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b94b1-111">Child Elements</span></span>  
  
|<span data-ttu-id="b94b1-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="b94b1-112">Element</span></span>|<span data-ttu-id="b94b1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b94b1-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="b94b1-114">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="b94b1-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b94b1-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b94b1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b94b1-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="b94b1-116">Element</span></span>|<span data-ttu-id="b94b1-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b94b1-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b94b1-118">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b94b1-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b94b1-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="b94b1-119">Example</span></span>  
 <span data-ttu-id="b94b1-120">Následující příklad ukazuje, jak používat  **\<mscorlib >** element tak, aby odkazovaly kryptografické třídy a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b94b1-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="b94b1-121">Řetězec "RSA" můžete poté předat do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použít <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metoda vrátí `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="b94b1-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b94b1-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b94b1-122">See Also</span></span>  
 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="b94b1-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b94b1-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="b94b1-124">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="b94b1-124">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="b94b1-125">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="b94b1-125">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="b94b1-126">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="b94b1-126">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
