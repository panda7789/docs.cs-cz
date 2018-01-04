---
title: "&lt;cryptoClasses –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 584b50da08eda5a3d40039a7702b24802f9d6388
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcryptoclassesgt-element"></a>&lt;cryptoClasses –&gt; – Element
Obsahuje seznam tříd šifrování, které mají mapování na popisného názvu do [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.  
  
 \<Konfigurace >  
\<mscorlib >  
\<cryptographySettings – >  
\<cryptoNameMapping >  
\<cryptoClasses – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<cryptoclass – >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|Obsahuje třídy šifrování, která má mapování na popisného názvu do  **\<nameEntry >** element.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`cryptographySettings`|Obsahuje nastavení šifrování.|  
|`cryptoNameMapping`|Obsahuje mapování třídy popisné názvy.|  
|`mscorlib`|Obsahuje `cryptographySettings` elementu.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat  **\<cryptoclass – >** element tak, aby odkazovaly kryptografické třídy a ke konfiguraci modulu runtime. Řetězec "RSA" můžete poté předat do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použít <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metoda vrátí `MyCryptoRSAClass` objektu.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Cryptography>  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Schéma nastavení šifrování](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [Kryptografické služby](../../../../../docs/standard/security/cryptographic-services.md)  
 [System.Security.Cryptography.CryptoConfig.CreateFromName](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)  
 [Konfigurace šifrovacích tříd](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
