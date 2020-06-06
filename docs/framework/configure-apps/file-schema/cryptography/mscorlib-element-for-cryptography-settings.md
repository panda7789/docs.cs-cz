---
title: <mscorlib> – element pro nastavení šifrování
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: d1d805f7154c18dba2dcd4eb7228cc200d8da811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155178"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="d722a-102">\<mscorlib> – element pro nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="d722a-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="d722a-103">Obsahuje [ \<cryptographySettings> element](cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="d722a-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<mscorlib>**  
  
## <a name="syntax"></a><span data-ttu-id="d722a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d722a-104">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d722a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d722a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d722a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d722a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d722a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="d722a-107">Attributes</span></span>  
 <span data-ttu-id="d722a-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="d722a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d722a-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d722a-109">Child Elements</span></span>  
  
|<span data-ttu-id="d722a-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="d722a-110">Element</span></span>|<span data-ttu-id="d722a-111">Description</span><span class="sxs-lookup"><span data-stu-id="d722a-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="d722a-112">Obsahuje nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="d722a-112">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d722a-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d722a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d722a-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="d722a-114">Element</span></span>|<span data-ttu-id="d722a-115">Description</span><span class="sxs-lookup"><span data-stu-id="d722a-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d722a-116">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d722a-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d722a-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="d722a-117">Example</span></span>  
 <span data-ttu-id="d722a-118">Následující příklad ukazuje, jak použít **\<mscorlib>** element k odkazování na třídu kryptografie a ke konfiguraci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d722a-118">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="d722a-119">Pak můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě a použít <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu k vrácení `MyCryptoRSAClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="d722a-119">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d722a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d722a-120">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="d722a-121">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d722a-121">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d722a-122">Schéma nastavení šifrování</span><span class="sxs-lookup"><span data-stu-id="d722a-122">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d722a-123">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="d722a-123">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="d722a-124">Konfigurace šifrovacích tříd</span><span class="sxs-lookup"><span data-stu-id="d722a-124">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
