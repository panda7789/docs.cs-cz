---
title: Vyberte verzi jazyka Visual Basic
description: Nakonfigurujte kompilátor provést ověření syntaxe pomocí specifické verzi kompilátoru.
ms.date: 05/24/2018
ms.openlocfilehash: 3b6d8055dbf64f2a5c38f46b6d66794fc48a1cea
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415101"
---
# <a name="select-the-visual-basic-language-version"></a>Vyberte verzi jazyka Visual Basic

Kompilátor jazyka Visual Basic výchozí nejnovější hlavní verzi jazyka, který byl vydán. Můžete se rozhodnout pro kompilaci libovolného projektu pomocí nové verze bodu jazyka. Výběr novější verzi jazyka umožňuje svým projektem zajistíte využívají nejnovější funkce jazyků. V jiných případech budete muset ověřit, že projekt zkompiluje čistě při používání starší verze jazyka.

Tato funkce odděluje rozhodnutí pro instalaci nové verze sady SDK a nástroje ve vašem vývojovém prostředí od rozhodnutí začlenit nové funkce jazyků v projektu. Nejnovější sady SDK a nástroje můžete nainstalovat na počítače pro sestavení. Každý projekt se dá použít konkrétní verzi jazyka pro jeho sestavení.

Existují tři způsoby, jak nastavit jazykovou verzi:

- Ručně upravit vaše [ **.vbproj** souboru](#edit-the-vbproj-file)
- Nastavit jazykovou verzi [pro více projektů v podadresáři](#configure-multiple-projects)
- Konfigurace [ `-langversion` – možnost kompilátoru](#set-the-langversion-compiler-option)

## <a name="edit-the-vbproj-file"></a>Upravte soubor vbproj

Můžete nastavit jazykovou verzi vašeho **.vbproj** souboru. Přidejte následující element:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Hodnota `latest` používá nejnovější dílčí verzi jazyka Visual Basic. Platné hodnoty jsou:

|Hodnota|Význam|
|------------|-------------|
|default|Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější hlavní verzi, která může podporovat.|
|9|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 9.0 nebo nižší.|
|10|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 10.0 nebo nižší.|
|11|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 11.0 nebo nižší.|
|12|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 12.0 nebo nižší.|
|14|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 14.0 nebo nižší.|
|15|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 15.0 nebo nižší.|
|15.3|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 15.3 nebo nižší.|
|15.5|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 15.5 nebo nižší.|
|nejnovější|Kompilátor přijímá všechny platné syntaxe jazyka, který může podporovat.|

Speciální řetězce `default` a `latest` přeložit na nejnovější hlavní a dílčí jazykové verze nainstalovaná v počítači sestavení, v uvedeném pořadí.

## <a name="configure-multiple-projects"></a>Konfigurace více projektů

Můžete vytvořit **Directory.build.props** soubor, který obsahuje `<LangVersion>` prvek, který chcete nakonfigurovat více adresářů. Obvykle to uděláte ve svém adresáři řešení. Přidejte následující text do **Directory.build.props** soubor v adresáři řešení:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

Nyní sestavení v každé podadresáře adresáře, který obsahuje tento soubor se syntaxí jazyka Visual Basic verze 15.5. Další informace najdete v článku na [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).

## <a name="set-the-langversion-compiler-option"></a>Nastavte langversion – možnost kompilátoru

Můžete použít `-langversion` možnost příkazového řádku. Další informace najdete v článku na [- langversion](../reference/command-line-compiler/langversion.md) – možnost kompilátoru. Seznam platných hodnot najdete tak, že zadáte `vbc -langversion:?` .
