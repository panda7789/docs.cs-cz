---
title: Element <cryptoClasses>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 89f1d89ea397794e366b53205ac23b94d7892869
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699758"
---
# <a name="cryptoclasses-element"></a>@no__t – element > 0cryptoClasses
Obsahuje seznam kryptografických tříd, které mají mapování na popisný název v prvku [\<nameEntry >](nameentry-element.md) .  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<cryptoClasses >**  
  
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
|[@no__t – 1cryptoClass >](cryptoclass-element.md)|Obsahuje třídu kryptografie, která má mapování na popisný název v prvku **\<nameEntry >** .|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`cryptographySettings`|Obsahuje nastavení kryptografie.|  
|`cryptoNameMapping`|Obsahuje mapování tříd na popisné názvy.|  
|`mscorlib`|Obsahuje prvek `cryptographySettings`.|  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography>
- [Schéma konfiguračního souboru](../index.md)
- [Schéma nastavení šifrování](index.md)
- [Kryptografické služby](../../../../standard/security/cryptographic-services.md)
- [System. Security. Cryptography. objektu CryptoConfig. CreateFromName](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [Konfigurace šifrovacích tříd](../../configure-cryptography-classes.md)
