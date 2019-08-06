---
title: C#jazykové verze – C# Průvodce
description: Přečtěte si informace C# o tom, jak je jazyková verze určena na základě vašeho projektu, a v různých hodnotách, na které lze ručně upravit.
ms.date: 07/10/2019
ms.openlocfilehash: 744cec0aac21f743648cccbdc93cf2977c32d644
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796529"
---
# <a name="c-language-versioning"></a>C#jazykové verze

C# Kompilátor určuje výchozí jazykovou verzi na základě cílových rozhraní architektury vašeho projektu nebo rozhraní. Důvodem je, že C# jazyk může obsahovat funkce, které spoléhají na typy nebo běhové komponenty, které nejsou k dispozici v každé implementaci rozhraní .NET. Tím se také zajistí, že pro jakýkoliv cíl, na který je projekt sestaven, získáte ve výchozím nastavení nejvyšší kompatibilní jazykovou verzi.

## <a name="defaults"></a>Ve výchozím nastavení

Kompilátor určuje výchozí hodnotu na základě těchto pravidel:

|Cílová architektura|verze|C#výchozí verze jazyka|
|----------------|-------|---------------------------|
|.NET Core|3.x|C#8,0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|všechny|C# 7.3|
|.NET Framework|všechny|C# 7.3|

## <a name="default-for-previews"></a>Výchozí pro náhledy

Když se váš projekt zaměřuje na architekturu verze Preview, která má odpovídající jazykovou verzi Preview, bude použit jazyk verze Preview. Tím zajistíte, že budete moci používat nejnovější funkce, u kterých je zaručená práce s touto verzí Preview v jakémkoli prostředí, aniž by to ovlivnilo projekty, které cílí na vydanou verzi .NET Core.

## <a name="override-a-default"></a>Přepsat výchozí

Pokud je nutné explicitně zadat C# verzi, můžete to provést několika způsoby:

- Ručně upravte [soubor projektu](#edit-the-project-file).
- Nastaví jazykovou verzi [pro více projektů v](#configure-multiple-projects)podadresáři.
- Konfigurovat [možnost kompilátoru `-langversion`](compiler-options/langversion-compiler-option.md)

### <a name="edit-the-project-file"></a>Upravit soubor projektu

V souboru projektu můžete nastavit jazykovou verzi. Například pokud výslovně chcete získat přístup k funkcím verze Preview, přidejte prvek podobný tomuto:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Hodnota `preview` používá nejnovější verzi verze Preview C# , kterou podporuje kompilátor.

### <a name="configure-multiple-projects"></a>Konfigurace více projektů

Můžete vytvořit soubor **Directory. Build. props** , který obsahuje `<LangVersion>` element pro konfiguraci více adresářů. Obvykle to provedete v adresáři řešení. Přidejte následující do souboru **Directory. Build. props** v adresáři řešení:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Nyní sestavení v každém podadresáři adresáře obsahujícího tento soubor použije verzi Preview C# . Další informace naleznete v článku o [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>C#Referenční informace o jazykové verzi

V následující tabulce jsou uvedeny všechny C# aktuální jazykové verze. Kompilátor nemusí nutně pochopit každou hodnotu, pokud je starší. Pokud nainstalujete .NET Core 3,0, budete mít přístup ke všem uvedeným.

|Value|Význam|
|------------|-------------|
|preview|Kompilátor přijímá všechny platné jazykové syntaxe z nejnovější verze Preview.|
|latest|Kompilátor přijímá syntaxi z nejnovější vydané verze kompilátoru (včetně dílčí verze).|
|latestMajor|Kompilátor přijímá syntaxi z poslední vydané hlavní verze kompilátoru.|
|8.0|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 8,0 nebo nižší.|
|7.3|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,3 nebo nižší.|
|7.2|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,2 nebo nižší.|
|7.1|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,1 nebo nižší.|
|7|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,0 nebo nižší.|
|6|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 6,0 nebo nižší.|
|5|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 5,0 nebo nižší.|
|4|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 4,0 nebo nižší.|
|3|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 3,0 nebo nižší.|
|ISO-2|Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2006 (2,0) |
|ISO-1|Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2003 (1.0/1.2) |
