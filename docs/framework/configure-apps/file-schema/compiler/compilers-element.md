---
title: Element <compilers>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155411"
---
# <a name="compilers-element"></a>\<kompilátory> Element
Kontejner pro konfigurační prvky kompilátoru; obsahuje nula [ \<](compiler-element.md) nebo více>prvků kompilátoru.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>kompilátorů**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<> element kompilátoru](compiler-element.md)|Určuje atributy konfigurace kompilátoru pro poskytovatele jazyka.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<konfigurace> Element](../configuration-element.md)|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|[\<system.codedom> Element](system-codedom-element.md)|Určuje nastavení konfigurace kompilátoru pro dostupné poskytovatele jazyků.|  
  
## <a name="remarks"></a>Poznámky  
 [ \<Kompilátory>](compilers-element.md) prvek obsahuje nastavení konfigurace kompilátoru pro poskytovatele jazyků v počítači. Každý [ \<prvek>kompilátoru](compiler-element.md) určuje atributy konfigurace kompilátoru pro konkrétního poskytovatele jazyka.  
  
 Rozhraní .NET Framework definuje počáteční nastavení kompilátoru a poskytovatele jazyka v konfiguračním souboru počítače (Machine.config). Vývojáři a dodavatelé kompilátoru <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> mohou přidat nastavení konfigurace pro novou implementaci. Pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> této metody můžete programově vytvořit výčet nastavení poskytovatele jazyka a konfigurace kompilátoru v počítači.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento prvek lze použít v konfiguračním souboru počítače a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje typický konfigurační prvek kompilátoru.  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler
          language="c#;cs;csharp"
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schéma konfiguračního souboru](../index.md)
- [Schéma nastavení kompilátoru a poskytovatele jazyka](index.md)
- [\<> element kompilátoru](compiler-element.md)
