---
title: Lokalizace
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
ms.openlocfilehash: 89851c42570f301bee8a3eca744eb5d069347d4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120871"
---
# <a name="localization"></a>Lokalizace

Lokalizace je proces překladu prostředků aplikace do lokalizovaných verzí pro každou jazykovou verzi, kterou bude aplikace podporovat. Krok lokalizace byste měli přejít až po dokončení kroku [Kontrola lokalizovatelnosti,](../../../docs/standard/globalization-localization/localizability-review.md) abyste ověřili, zda je globalizovaná aplikace připravena k lokalizaci.

Aplikace, která je připravena k lokalizaci, je rozdělena do dvou koncepčních bloků: blok, který obsahuje všechny prvky uživatelského rozhraní, a blok, který obsahuje spustitelný kód. Blok uživatelského rozhraní obsahuje pouze lokalizovatelné prvky uživatelského rozhraní, jako jsou řetězce, chybové zprávy, dialogová okna, nabídky, vložené prostředky objektů a tak dále pro neutrální jazykovou verzi. Blok kódu obsahuje pouze kód aplikace, který má být použit všemi podporovanými jazyky. Modul COMMON Language runtime podporuje model prostředků satelitního sestavení, který odděluje spustitelný kód aplikace od jejích prostředků. Další informace o implementaci tohoto modelu naleznete v tématu [Prostředky v rozhraní .NET](../../../docs/framework/resources/index.md).

Pro každou lokalizovanou verzi aplikace přidejte nové satelitní sestavení, které obsahuje blok lokalizovaného uživatelského rozhraní přeložený do příslušného jazyka pro cílovou jazykovou verzi. Blok kódu pro všechny jazykové verze by měl zůstat stejný. Kombinace lokalizované verze bloku uživatelského rozhraní s blokem kódu vytváří lokalizovanou verzi aplikace.

Sada SDK (Windows Software Development Kit) poskytuje editor prostředků systému Windows Forms (Winres.exe), který umožňuje rychle lokalizovat formuláře Systému Windows pro cílové jazykové verze. Informace o použití tohoto nástroje naleznete v [tématu Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).

## <a name="see-also"></a>Viz také

- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
- [Kontrola lokalizovatelnosti](../../../docs/standard/globalization-localization/localizability-review.md)
- [Globalizace](../../../docs/standard/globalization-localization/globalization.md)
- [Prostředky v aplikacích klasické pracovní plochy](../../../docs/framework/resources/index.md)
