---
title: Element <cryptoClass>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: db3681ea141bb7e3905f6a470f5c74ce05f6ef4b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699790"
---
# <a name="cryptoclass-element"></a>@no__t – element > 0cryptoClass
Obsahuje třídu kryptografie, která má mapování na popisný název v prvku [\<nameEntry >](nameentry-element.md) .  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0cryptoClasses >** ](cryptoclasses-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1cryptoClass >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`customClassName`|Požadovaný atribut.<br /><br /> Obsahuje informace pro třídu kryptografie. Tento atribut slouží k zadání krátkého názvu vaší třídy. Je nutné zadat řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`cryptoClasses`|Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v prvku [\<nameEntry >](nameentry-element.md) .|  
|`cryptographySettings`|Obsahuje nastavení kryptografie.|  
|`cryptoNameMapping`|Obsahuje mapování tříd na popisné názvy.|  
|`mscorlib`|Obsahuje prvek [> \<cryptographySettings](cryptographysettings-element.md) .|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít prvek **> \<cryptoClass** k odkazování na třídu kryptografie a ke konfiguraci modulu runtime. Pak můžete předat řetězec "RSA" metodě <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> a použít metodu <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pro vrácení objektu `MyCryptoRSAClass`.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../index.md)
- [Schéma nastavení šifrování](index.md)
- [Kryptografické služby](../../../../standard/security/cryptographic-services.md)
- [Konfigurace šifrovacích tříd](../../configure-cryptography-classes.md)
