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
ms.openlocfilehash: d8f4d4aa9c80990cdf858da9fcdf6465438866cf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927564"
---
# <a name="nameentry-element"></a>\<nameEntry – element >
Mapuje název třídy na popisný název algoritmu, který umožňuje, aby jedna třída měla mnoho popisných názvů.  
  
 \<> Konfigurace  
\<mscorlib>  
\<cryptographySettings >  
\<cryptoNameMapping>  
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
|**name**|Požadovaný atribut.<br /><br /> Určuje popisný název algoritmu, který kryptografická třída implementuje.|  
|**class**|Požadovaný atribut.<br /><br /> Určuje hodnotu atributu **Name** v [ \<elementu cryptoClass >](cryptoclass-element.md) .|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.web`|Určuje kořenový element konfiguračního oddílu ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
 Atribut **Name** může být název jedné z abstraktních tříd nalezených v <xref:System.Security.Cryptography> oboru názvů. Při volání metody **Create** na abstraktní kryptografické třídě je název abstraktní třídy předán <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metodě. **CreateFromName** vrací instanci typu, která je označena atributem **Class** . Pokud je atribut **Name** krátkým názvem, jako je například RSA, můžete použít tento název při volání metody **CreateFromName** .  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití  **\<prvku nameEntry >** k odkazování na třídu kryptografie a ke konfiguraci modulu runtime. Pak můžete předat řetězec "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metodě a <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> použít metodu k vrácení `MyCryptoRSAClass` objektu.  
  
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
