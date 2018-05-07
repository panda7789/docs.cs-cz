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
ms.openlocfilehash: 7fc995843c1e2f5977acbfe2158457d30ac355ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="localization"></a>Lokalizace
Lokalizace je proces převodu aplikace prostředky do lokalizované verze pro každou jazykovou verzi, která bude podporovat aplikace. Až po dokončení byste měli přistoupit k lokalizaci [lokalizovatelnosti](../../../docs/standard/globalization-localization/localizability-review.md) kroku ověřte, že globalizovaná aplikace je připravena k lokalizaci.  
  
 Aplikace, která je připravena k lokalizaci je rozdělené do dvou konceptuálních bloků, blok, který obsahuje všechny prvky uživatelského rozhraní a blok, který obsahuje spustitelný kód. Bloky uživatelského rozhraní obsahuje pouze možnosti lokalizace uživatelského rozhraní prvky, jako jsou například řetězce, chybové zprávy, dialogových oken, nabídek, vložený objekt prostředky, a tak dále pro neutrální jazykovou verzi. Blok kódu obsahuje pouze kódu aplikace má být používána všechny podporované jazykové verze. Modul common language runtime podporuje model prostředků satelitních sestavení, oddělující spustitelný kód aplikace ze svých prostředků. Další informace o implementaci tohoto modelu najdete v tématu [prostředků v aplikacích plochy](../../../docs/framework/resources/index.md).  
  
 Pro každou lokalizované verzi vaší aplikace přidáte nové satelitní sestavení, který obsahuje lokalizované uživatelské rozhraní bloku přeložit na příslušném jazyku u cílové jazykové verzi. Blok kódu pro všechny jazykové verze by měla zůstat stejné. Kombinace lokalizované verze bloku uživatelského rozhraní s blok kódu vytvoří lokalizovanou verzi vaší aplikace.  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Dodává nástroj Windows Forms prostředků Editor (Winres.exe), který umožňuje rychle lokalizovat Windows Forms do cílové jazykové verze. Informace o použití tohoto nástroje najdete v tématu [Winres.exe (Editor prostředků Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).  
  
## <a name="see-also"></a>Viz také  
 [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)  
 [Vyhodnocení lokalizovatelnosti](../../../docs/standard/globalization-localization/localizability-review.md)  
 [Globalizace](../../../docs/standard/globalization-localization/globalization.md)  
 [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
