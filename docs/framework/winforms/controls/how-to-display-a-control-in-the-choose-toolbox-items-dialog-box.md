---
title: 'Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9a6938b4fe651e13f3ec96642db6027143f1f028
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015886"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů

Při vývoji a distribuci ovládacích prvků můžete chtít, aby se tyto ovládací prvky zobrazovaly v dialogovém okně **zvolit položky sady nástrojů** sady Visual Studio, které se zobrazí po kliknutí pravým tlačítkem myši na **panel nástrojů** a vybrání možnosti **zvolit položky**. Můžete povolit, aby se váš ovládací prvek zobrazil v tomto dialogovém okně pomocí postupu registrace AssemblyFoldersEx.

Chcete-li zobrazit ovládací prvek v dialogovém okně zvolit položky sady nástrojů:

- Nainstalujte sestavení ovládacího prvku do globální mezipaměti sestavení (GAC). Další informace najdete v tématu [jak: Instalace sestavení do globální mezipaměti sestavení (GAC)](../../app-domains/how-to-install-an-assembly-into-the-gac.md)

  -nebo-

- Zaregistrujte svůj ovládací prvek a jeho přidružená sestavení v době návrhu pomocí postupu registrace AssemblyFoldersEx. AssemblyFoldersEx je umístění v registru, kde dodavatelé třetích stran ukládají cesty pro každou verzi rozhraní, kterou podporují. Rozlišení v době návrhu může vyhledat referenční sestavení v tomto umístění registru. Skript registru může určovat ovládací prvky, které se mají zobrazit v sadě nástrojů.

## <a name="see-also"></a>Viz také:

- [Vývoj ovládacích prvků Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)
- [Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC)](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
