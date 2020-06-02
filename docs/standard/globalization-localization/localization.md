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
ms.openlocfilehash: 68e877088c5c3d17b368561b563b4cb17d004e75
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278022"
---
# <a name="localization"></a>Lokalizace

Lokalizace je proces překladu prostředků aplikace na lokalizované verze pro každou jazykovou verzi, kterou bude aplikace podporovat. Do kroku lokalizace byste měli přejít až po dokončení kroku [kontroly lokalizace](localizability-review.md) , abyste ověřili, že je globální aplikace připravená na lokalizaci.

Aplikace, která je připravena k lokalizaci, je rozdělena do dvou koncepčních bloků: blok, který obsahuje všechny prvky uživatelského rozhraní a blok, který obsahuje spustitelný kód. Blok uživatelského rozhraní obsahuje pouze lokalizovatelné prvky uživatelského rozhraní, jako jsou například řetězce, chybové zprávy, dialogová okna, nabídky, vložené objekty objektů a tak dále pro neutrální jazykovou verzi. Blok kódu obsahuje pouze kód aplikace, který bude používán všemi podporovanými kulturami. Modul CLR (Common Language Runtime) podporuje model prostředků satelitního sestavení, který odděluje spustitelný kód aplikace od jeho prostředků. Další informace o implementaci tohoto modelu naleznete v tématu [prostředky v rozhraní .NET](../../framework/resources/index.md).

Pro každou lokalizovanou verzi vaší aplikace přidejte nové satelitní sestavení, které obsahuje lokalizovaný blok uživatelského rozhraní přeložený do příslušného jazyka pro cílovou jazykovou verzi. Blok kódu pro všechny jazykové verze by měl zůstat stejný. Kombinace lokalizované verze bloku uživatelského rozhraní s blokem kódu vytváří lokalizovanou verzi aplikace.

Sada Windows Software Development Kit (SDK) poskytuje editor prostředků model Windows Forms (Winres. exe), který umožňuje rychle lokalizovat model Windows Forms pro cílové jazykové verze. Informace o použití tohoto nástroje naleznete v tématu [Winres. exe (model Windows Forms editor prostředků)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).

## <a name="see-also"></a>Viz také

- [Globalizace a lokalizace](index.md)
- [Kontrola lokalizovatelnosti](localizability-review.md)
- [Globalizace](globalization.md)
- [Prostředky v aplikacích klasické pracovní plochy](../../framework/resources/index.md)
