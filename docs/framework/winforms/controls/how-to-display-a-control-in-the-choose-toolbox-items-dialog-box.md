---
title: 'Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů'
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db4b3ac020e967a6a0c291103d825ac71cebda23
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458282"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů

Při vývoji a distribuci ovládacích prvků můžete chtít, aby se tyto ovládací prvky zobrazovaly v dialogovém okně **zvolit položky sady nástrojů** sady Visual Studio, které se zobrazí po kliknutí pravým tlačítkem myši na **panel nástrojů** a vybrání možnosti **zvolit položky**. Můžete povolit, aby se váš ovládací prvek zobrazil v tomto dialogovém okně pomocí postupu registrace AssemblyFoldersEx.

Chcete-li zobrazit ovládací prvek v dialogovém okně zvolit položky sady nástrojů:

- Nainstalujte sestavení ovládacího prvku do globální mezipaměti sestavení (GAC). Další informace naleznete v tématu [Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC](../../app-domains/install-assembly-into-gac.md)).

  -nebo-

- Zaregistrujte svůj ovládací prvek a jeho přidružená sestavení v době návrhu pomocí postupu registrace AssemblyFoldersEx. AssemblyFoldersEx je umístění v registru, kde dodavatelé třetích stran ukládají cesty pro každou verzi rozhraní, kterou podporují. Rozlišení v době návrhu může vyhledat referenční sestavení v tomto umístění registru. Skript registru může určovat ovládací prvky, které se mají zobrazit v sadě nástrojů.

## <a name="see-also"></a>Viz také:

- [Vývoj ovládacích prvků Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)
- [Postupy: Instalace sestavení do globální mezipaměti sestavení](../../app-domains/install-assembly-into-gac.md)
- [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
