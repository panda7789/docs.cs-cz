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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79ec24d16b43bd8e1312b3425e618adf163edd24
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834027"
---
# <a name="localization"></a>Lokalizace

Lokalizace je proces převodu aplikační prostředky do lokalizované verze pro každou jazykovou verzi, která bude podporovat aplikace. By měl pokračujte krokem lokalizace až po dokončení [přezkoumání lokalizovatelnosti](../../../docs/standard/globalization-localization/localizability-review.md) kroku ověřte, že globalizovaná aplikace je připravena k lokalizaci.

Aplikace, která jsou připravená pro lokalizaci rozdělen do dvou bloků koncepční: blok, který obsahuje všechny prvky uživatelského rozhraní a blok, který obsahuje spustitelný kód. Bloky uživatelského rozhraní obsahuje pouze lokalizovatelné uživatelského rozhraní prvky, jako jsou řetězce, chybové zprávy, dialogová okna, nabídek, prostředky vložených objektů a podobně pro neutrální jazykovou verzi. Blok kódu obsahuje pouze kód aplikace, které bude využívat všechny podporované jazykové verze. Modul common language runtime podporuje model prostředků satelitních sestavení, oddělující spustitelného kódu vaší aplikace z jejích prostředků. Další informace o implementaci tohoto modelu najdete v tématu [prostředky v prostředí .NET](../../../docs/framework/resources/index.md).

Pro každou lokalizovanou verzi vaší aplikace přidáte nové satelitní sestavení, který obsahuje blok lokalizovaná uživatelská rozhraní přeložit na příslušný jazyk cílové jazykové verze. Blok kódu pro všechny jazykové verze by měla zůstat stejná. Kombinace lokalizovanou verzi bloku uživatelského rozhraní s blok kódu vytvoří lokalizovanou verzi vaší aplikace.

Windows Software Development Kit (SDK) poskytuje nástroj Windows Forms Resource Editor (Winres.exe), umožňující rychle lokalizovat formuláře Windows pro cílové jazykové verze. Informace o použití tohoto nástroje najdete v tématu [Winres.exe (Editor prostředků Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).

## <a name="see-also"></a>Viz také:

- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
- [Vyhodnocení lokalizovatelnosti](../../../docs/standard/globalization-localization/localizability-review.md)
- [Globalizace](../../../docs/standard/globalization-localization/globalization.md)
- [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
