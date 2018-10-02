---
title: '&lt;mscorlib&gt; – Element pro nastavení kryptografie'
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
ms.openlocfilehash: b5da49ff22cfa6bd1c3e4d574865eb5e61dc73fb
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028353"
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a><span data-ttu-id="841be-102">&lt;mscorlib&gt; – Element pro nastavení kryptografie</span><span class="sxs-lookup"><span data-stu-id="841be-102">&lt;mscorlib&gt; Element for Cryptography Settings</span></span>
<span data-ttu-id="841be-103">Obsahuje [ \<cryptographySettings – > element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="841be-103">Contains the [\<cryptographySettings> element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="841be-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="841be-104">\<configuration></span></span>  
<span data-ttu-id="841be-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="841be-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="841be-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="841be-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="841be-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="841be-107">Attributes and Elements</span></span>  
 <span data-ttu-id="841be-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="841be-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="841be-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="841be-109">Attributes</span></span>  
 <span data-ttu-id="841be-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="841be-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="841be-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="841be-111">Child Elements</span></span>  
  
|<span data-ttu-id="841be-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="841be-112">Element</span></span>|<span data-ttu-id="841be-113">Popis</span><span class="sxs-lookup"><span data-stu-id="841be-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="841be-114">Obsahuje nastavení šifrování.</span><span class="sxs-lookup"><span data-stu-id="841be-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="841be-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="841be-115">Parent Elements</span></span>  
  
|<span data-ttu-id="841be-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="841be-116">Element</span></span>|<span data-ttu-id="841be-117">Popis</span><span class="sxs-lookup"><span data-stu-id="841be-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="841be-118">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="841be-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="841be-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="841be-119">Example</span></span>  
 <span data-ttu-id="841be-120">Následující příklad ukazuje způsob použití  **\<mscorlib >** element tak, aby odkazovaly kryptografickou třídu a konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="841be-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="841be-121">Můžete poté předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použití <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu pro návrat `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="841be-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="841be-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="841be-122">See Also</span></span>  
 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="841be-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="841be-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="841be-124">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="841be-124">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="841be-125">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="841be-125">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="841be-126">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="841be-126">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
