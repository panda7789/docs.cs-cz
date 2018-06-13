---
title: '&lt;cryptoclass –&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 728fff7b8626e227e692c713f4cb05049c14a9f1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742754"
---
# <a name="ltcryptoclassgt-element"></a>&lt;cryptoclass –&gt; – Element
Obsahuje třídy šifrování, která má mapování na popisného názvu do [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.  
  
 \<Konfigurace >  
\<mscorlib >  
\<cryptographySettings – >  
\<cryptoNameMapping >  
\<cryptoClasses – >  
\<cryptoclass – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`customClassName`|Požadovaný atribut.<br /><br /> Obsahuje informace o třídě šifrování. Pomocí tohoto atributu zadejte krátký název pro vlastní třídy. Zadejte řetězec, který splňuje požadavky uvedené v [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`cryptoClasses`|Obsahuje seznam tříd šifrování, které mají mapování na popisného názvu do [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.|  
|`cryptographySettings`|Obsahuje nastavení šifrování.|  
|`cryptoNameMapping`|Obsahuje mapování třídy popisné názvy.|  
|`mscorlib`|Obsahuje [ \<cryptographySettings – >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) element.|  
  
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
