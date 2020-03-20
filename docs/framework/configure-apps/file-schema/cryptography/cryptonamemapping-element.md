---
title: Element <cryptoNameMapping>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: d31c5cd52ffe0e2a6eb5784735e76436d216444b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155216"
---
# <a name="cryptonamemapping-element"></a>\<kryptonamemapping> element
Obsahuje mapování tříd na popisné názvy.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<kryptografieNastavení>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<kryptonamemapping>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`cryptoClasses`|Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v ** \<elementu nameEntry>.**|  
|`nameEntry`|Mapuje název třídy na popisný název algoritmu, který umožňuje jedné třídě mít mnoho popisných názvů.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`cryptographySettings`|Obsahuje nastavení kryptografie.|  
|`cryptoNameMapping`|Obsahuje mapování tříd na popisné názvy.|  
|`mscorlib`|Obsahuje \<kryptografiiNastavení> prvek.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat element ** \<cryptoNameMapping>** k odkazování na kryptografickou třídu a ke konfiguraci runtime. Potom můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> a použít `MyCryptoRSAClass` metodu k vrácení objektu.  
  
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

- [Schéma konfiguračního souboru](../index.md)
- [Schéma nastavení šifrování](index.md)
- [Kryptografické služby](../../../../standard/security/cryptographic-services.md)
- [Konfigurace šifrovacích tříd](../../configure-cryptography-classes.md)
