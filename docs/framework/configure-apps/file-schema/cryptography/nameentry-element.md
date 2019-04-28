---
title: Element <nameEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 97521ba9073820beeea62f5fc7cab480b5422fb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705178"
---
# <a name="nameentry-element"></a>\<nameEntry – > – Element
Název třídy mapuje na algoritmus popisný název, který umožňuje jedna třída má mnoho popisné názvy.  
  
 \<Konfigurace >  
\<mscorlib>  
\<cryptographySettings>  
\<cryptoNameMapping>  
\<nameEntry – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**Jméno**|Požadovaný atribut.<br /><br /> Určuje popisný název algoritmu, který implementuje kryptografickou třídu.|  
|**class**|Požadovaný atribut.<br /><br /> Určuje hodnotu **název** atribut [ \<cryptoclass – >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) elementu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.web`|Určuje kořenový element části o konfiguraci technologie ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
 **Název** atribut může být název jedné z abstraktní třídy součástí <xref:System.Security.Cryptography> oboru názvů. Při volání **vytvořit** metoda abstract kryptografickou třídu, název abstraktní třídy je předán <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metody. **CreateFromName** vrací instanci typu indikován **třídy** atribut. Pokud **název** atribut je krátký název, třeba RSA, můžete použít tento název při volání **CreateFromName** metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití  **\<nameEntry >** element tak, aby odkazovaly kryptografickou třídu a konfigurace modulu runtime. Můžete poté předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda a použití <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodu pro návrat `MyCryptoRSAClass` objektu.  
  
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

- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Schéma nastavení šifrování](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [Kryptografické služby](../../../../../docs/standard/security/cryptographic-services.md)
- [Konfigurace šifrovacích tříd](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
