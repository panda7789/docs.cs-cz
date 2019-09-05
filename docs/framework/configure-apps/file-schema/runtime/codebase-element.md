---
title: Element <codeBase>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: bd170b817c5ccc337711f8f79968653c29f3eda4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252748"
---
# <a name="codebase-element"></a>\<> – element codeBase

Určuje, kde modul CLR (Common Language Runtime) může najít sestavení.

[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dependentAssembly**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<codeBase>**

## <a name="syntax"></a>Syntaxe

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`href`|Požadovaný atribut.<br /><br /> Určuje adresu URL, kde může modul runtime najít určenou verzi sestavení.|
|`version`|Požadovaný atribut.<br /><br /> Určuje verzi sestavení, na kterou se základ kódu vztahuje. Formát čísla verze sestavení je *hlavní_verze. podverze. sestavení. revize*.|

## <a name="version-attribute"></a>Atribut Version

|Value|Popis|
|-----------|-----------------|
|Platné hodnoty pro každou část čísla verze jsou 0 až 65535.|Není k dispozici.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|`buildproviders`|Definuje kolekci poskytovatelů sestavení použitých ke kompilaci vlastních souborů prostředků. Můžete mít libovolný počet poskytovatelů sestavení.|
|`compilation`|Konfiguruje všechna nastavení kompilace, která ASP.NET používá.|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`System.web`|Určuje kořenový element konfiguračního oddílu ASP.NET.|

## <a name="remarks"></a>Poznámky

Aby modul runtime používal  **\<>** nastavení v konfiguračním souboru počítače nebo souboru zásad vydavatele, soubor musí také přesměrovat verzi sestavení. Konfigurační soubory aplikace mohou mít nastavení základu kódu bez přesměrování verze sestavení. Po určení používané verze sestavení používá modul runtime nastavení základu kódu ze souboru, který určuje verzi. Pokud není uveden žádný základ kódu, běhové testy pro sestavení obvyklým způsobem.

Pokud má sestavení silný název, může být nastavení základu kdekoli na místním intranetu nebo Internetu. Pokud je sestavení privátní sestavení, musí být nastavení základu cesty relativní vzhledem k adresáři aplikace.

U sestavení bez silného názvu je verze ignorována a zavaděč používá první vzhled \<základu kódu > uvnitř \<dependentAssembly >. Pokud existuje položka v konfiguračním souboru aplikace, která přesměrovává vazby na jiné sestavení, přesměrování bude mít přednost i v případě, že verze sestavení neodpovídá požadavku vazby.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak určit, kde modul runtime může najít sestavení.

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly"
                              publicKeyToken="32ab4ba45e0a69a1"
                              culture="neutral" />
            <codeBase version="2.0.0.0"
                      href="http://www.litwareinc.com/myAssembly.dll"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Určení umístění sestavení](../../specify-assembly-location.md)
- [Jak běhové prostředí vyhledává sestavení](../../../deployment/how-the-runtime-locates-assemblies.md)
