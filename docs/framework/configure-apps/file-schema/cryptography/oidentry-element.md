---
title: Element <oidEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 4564cf59e3b6cfbdcd9dca06cd0f966d524834de
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088550"
---
# <a name="oidentry-element"></a>\<element > oidEntry
Mapuje identifikátor objektu ASN. 1 (OID) na popisný název.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidMap >** ](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<oidEntry >**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**IDENTIFIKÁTOR**|Požadovaný atribut.<br /><br /> Určuje ID ASN. 1, které odpovídá algoritmu implementovanému vaší třídou.|  
|**Jméno**|Požadovaný atribut.<br /><br /> Určuje hodnotu atributu **název** ve značce [\<nameEntry >](nameentry-element.md) .|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`cryptographySettings`|Obsahuje nastavení kryptografie.|  
|`mscorlib`|Obsahuje element `cryptographySettings`.|  
|`oidMap`|Obsahuje mapování identifikátoru objektu ASN. 1 na třídy.|  
  
## <a name="remarks"></a>Poznámky  
 Identifikátory objektů ASN. 1 identifikují algoritmy v některých kryptografických formátech. Namapujte identifikátory objektů na popisné názvy algoritmů, které chcete identifikovat.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití prvku **\<oidEntry >** k mapování identifikátoru objektu pro algoritmus hash RIPEMD-160 na implementaci tohoto algoritmu hash.  
  
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
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../index.md)
- [Schéma nastavení šifrování](index.md)
- [Kryptografické služby](../../../../standard/security/cryptographic-services.md)
- [Konfigurace šifrovacích tříd](../../configure-cryptography-classes.md)
- [Mapování identifikátorů objektů na algoritmy šifrování](../../map-object-identifiers-to-cryptography-algorithms.md)
