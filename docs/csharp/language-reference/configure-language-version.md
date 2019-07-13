---
title: C#Správa verzí jazyka - C# Průvodce
description: Další informace o tom, jak C# jazykové verze je určena na základě vašeho projektu a jiné hodnoty lze upravit ručně ji.
ms.date: 07/10/2019
ms.openlocfilehash: 2d593ca0588f291c61cdf52fbc1eb60a1f3f7ecb
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859601"
---
# <a name="c-language-versioning"></a>C#Správa verzí jazyka

C# Kompilátor Určuje výchozí jazykovou verzi na základě cílové rozhraní projektu nebo rozhraní. Je to proto, C# jazyka může mít funkce, které závisí na typech nebo runtime komponenty, které nejsou k dispozici v každé implementace .NET. To také zajistí, že pro jakékoli cílové váš projekt se vytvořil proti, dostanete nejvyšší verze kompatibilní jazyka ve výchozím nastavení.

## <a name="defaults"></a>Ve výchozím nastavení

Kompilátor Určuje výchozí na základě těchto pravidel:

|Cílová architektura|verze|C#Výchozí verze jazyka|
|----------------|-------|---------------------------|
|.NET Core|3.x|C#8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|všechny|C# 7.3|
|.NET Framework|všechny|C# 7.3|

## <a name="default-for-previews"></a>Výchozí nastavení pro verze Preview

Když váš projekt cílí na verzi preview rozhraní, které obsahuje odpovídající jazykovou verzi preview, je jazyková verze používá jazykovou verzi preview. Tím se zajistí, že můžete použít nejnovější funkce, které jsou zaručeny pracovat v této verzi preview v jakémkoli prostředí bez ovlivnění vašich projektů cílených vydanou verzi .NET Core.

## <a name="overriding-a-default"></a>Přepsání výchozího

Pokud je nutné zadat vaše C# verze explicitně, lze provést několika způsoby:

- Ručně upravit vaše [soubor projektu](#edit-the-project-file).
- Nastavit jazykovou verzi [pro více projektů v podadresáři](#configure-multiple-projects).
- Konfigurace [ `-langversion` – možnost kompilátoru](#set-the-langversion-compiler-option).

### <a name="edit-the-project-file"></a>Úprava souboru projektu

V souboru projektu můžete nastavit jazykovou verzi. Například pokud chcete explicitně přístup k funkce ve verzi preview, můžete přidat element následujícím způsobem:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Hodnota `preview` používá nejnovější dostupné verze preview C# jazyk, který kompilátor podporuje.

### <a name="configure-multiple-projects"></a>Konfigurace více projektů

Můžete vytvořit **Directory.Build.props** soubor, který obsahuje `<LangVersion>` prvek, který chcete nakonfigurovat více adresářů. Obvykle to uděláte ve svém adresáři řešení. Přidejte následující text do **Directory.Build.props** soubor v adresáři řešení:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Nyní, sestavení v každé podadresáře adresáře, který obsahuje tento soubor bude používat verzi preview C# verze. Další informace najdete v článku na [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>C#referenční informace k jazyku verze

V následující tabulce jsou uvedeny všechny aktuální C# jazykové verze. Váš kompilátor nemusí pochopit nutně každá hodnota, pokud je starší. Pokud nainstalujete .NET Core 3.0, bude mít přístup ke všemu, co jsou uvedeny.

|Value|Význam|
|------------|-------------|
|preview|Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější verze preview.|
|latest|Kompilátor přijímá syntaxi z nejnovější vydanou verzi kompilátoru (včetně vedlejší verze aktualizace).|
|latestMajor|Kompilátor přijímá syntaxi z nejnovější vydanou hlavní verzi kompilátoru.|
|8.0|Kompilátor přijímá pouze syntaxi, která je součástí C# 8.0 nebo nižší.|
|7.3|Kompilátor přijímá pouze syntaxi, která je součástí C# 7.3 nebo nižší.|
|7.2|Kompilátor přijímá pouze syntaxi, která je součástí C# 7.2 nebo nižší.|
|7.1|Kompilátor přijímá pouze syntaxi, která je součástí C# 7.1 nebo nižší.|
|7|Kompilátor přijímá pouze syntaxi, která je součástí C# 7.0 nebo nižší.|
|6|Kompilátor přijímá pouze syntaxi, která je součástí C# 6.0 nebo nižší.|
|5|Kompilátor přijímá pouze syntaxi, která je součástí C# 5.0 nebo nižší.|
|4|Kompilátor přijímá pouze syntaxi, která je součástí C# 4.0 nebo nižší.|
|3|Kompilátor přijímá pouze syntaxi, která je součástí C# 3.0 nebo nižší.|
|ISO-2|Kompilátor přijímá pouze syntaxi, která je součástí 23270: ISO/IEC 2006 C# (2.0) |
|ISO-1|Kompilátor přijímá pouze syntaxi, která je součástí 23270: ISO/IEC 2003 C# (1.0 nebo 1.2) |
