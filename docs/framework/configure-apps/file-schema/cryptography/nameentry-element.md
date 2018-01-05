---
title: "&lt;nameEntry –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7c9a4b4532d98b7dfc2484dab1bb57e5a26fa392
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltnameentrygt-element"></a>&lt;nameEntry –&gt; – Element
Mapuje název třídy algoritmus popisný název, který umožňuje jednu třídu k mít mnoho popisné názvy.  
  
 \<Konfigurace >  
\<mscorlib >  
\<cryptographySettings – >  
\<cryptoNameMapping >  
\<nameEntry >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**Jméno**|Požadovaný atribut.<br /><br /> Určuje popisný název algoritmu, který implementuje třídu šifrování.|  
|**class**|Požadovaný atribut.<br /><br /> Určuje hodnotu **název** atribut [ \<cryptoclass – >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.web`|Určuje kořenový element pro konfigurační oddíl technologie ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
 **Název** atributu může být název jednoho z abstraktní třídy, které jsou součástí <xref:System.Security.Cryptography> oboru názvů. Při volání **vytvořit** metoda u kryptografie abstraktní třídy název abstraktní třídy je předána <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metoda. **CreateFromName** vrací instanci typu indikován **třída** atribut. Pokud **název** atribut je krátký název, jako je například RSA, můžete použít tento název při volání metody **CreateFromName** metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat  **\<nameEntry >** element tak, aby odkazovaly kryptografické třídy a ke konfiguraci modulu runtime. Řetězec "RSA" můžete poté předat do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použít <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metoda vrátí `MyCryptoRSAClass` objektu.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Schéma nastavení šifrování](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [Kryptografické služby](../../../../../docs/standard/security/cryptographic-services.md)  
 [Konfigurace šifrovacích tříd](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
