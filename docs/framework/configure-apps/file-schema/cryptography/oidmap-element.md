---
title: Element <oidMap>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: a28eaf68fe1e6ab3f26592eee5ae2d0f2e7a3256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155164"
---
# <a name="oidmap-element"></a>\<Map> prvek
Obsahuje mapování identifikátorů objektu ASN.1 (OID) na třídy.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<kryptografieNastavení>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|Mapuje OID ASN.1 na popisný název.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`cryptographySettings`|Obsahuje nastavení kryptografie.|  
|`mscorlib`|Obsahuje `cryptographySettings` prvek.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít ** \<oidMap>** prvek obsahovat mapování OID pro algoritmus hash RIPEMD-160 na implementaci tohoto algoritmu hash.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru](../index.md)
- [Schéma nastavení šifrování](index.md)
- [Kryptografické služby](../../../../standard/security/cryptographic-services.md)
- [Konfigurace šifrovacích tříd](../../configure-cryptography-classes.md)
- [Mapování identifikátorů objektů na algoritmy šifrování](../../map-object-identifiers-to-cryptography-algorithms.md)
