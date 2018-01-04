---
title: "&lt;mscorlib&gt; Element pro nastavení kryptografie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 18948d538b01304e90cac3b36988ccf29a586da0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a>&lt;mscorlib&gt; Element pro nastavení kryptografie
Obsahuje [ \<cryptographySettings – > element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).  
  
 \<Konfigurace >  
\<mscorlib >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`cryptographySettings`|Obsahuje nastavení šifrování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat  **\<mscorlib >** element tak, aby odkazovaly kryptografické třídy a ke konfiguraci modulu runtime. Řetězec "RSA" můžete poté předat do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použít <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metoda vrátí `MyCryptoRSAClass` objektu.  
  
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
 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>  
 <xref:System.Security.Cryptography>  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Schéma nastavení šifrování](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [Kryptografické služby](../../../../../docs/standard/security/cryptographic-services.md)  
 [Konfigurace šifrovacích tříd](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
