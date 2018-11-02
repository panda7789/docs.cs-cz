---
title: Zabezpečení zprostředkovatele typů
description: 'Další informace o zabezpečení zprostředkovatele typů v jazyce F #, včetně postupu, chcete-li změnit nastavení vztahu důvěryhodnosti pro poskytovatele typu.'
ms.date: 05/16/2016
ms.openlocfilehash: 26f95ad3950b37a668c497f293b9941ed13a18c7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43861904"
---
# <a name="type-provider-security"></a>Zabezpečení zprostředkovatele typů

Poskytovatelé typů jsou sestavení (knihovny DLL) odkazovaných projektů F # nebo skriptů, které obsahují kód k připojení k externím zdrojům dat a poskytování informací o tomto typu prostředí typů F #. Kód v odkazovaných sestaveních je obvykle spustit jenom při kompilaci a potom spusťte kód (nebo v případě skript, odeslat kód do F # Interactive). Sestavení zprostředkovatele typu však bude fungovat v sadě Visual Studio při procházení kódu pouze v editoru. K tomu dochází, protože typ poskytovatele potřebné ke přidat dodatečné informace k editoru, jako je například popisky rychlé informace, dokončování IntelliSense a tak dále. V důsledku toho některé další bezpečnostní aspekty pro typ sestavení zprostředkovatele, protože jejich automaticky spuštěn uvnitř procesu Visual Studio.

## <a name="security-warning-dialog"></a>Dialogové okno upozornění zabezpečení

Při prvním použití sestavení zprostředkovatele na určitý typ, Visual Studio zobrazí dialogové okno zabezpečení, která vás upozorní, že zprostředkovatel typu je spuštěn. Před Visual Studio načte typ zprostředkovatele, dává možnost rozhodnout, zda důvěřovat tohoto konkrétního zprostředkovatele. Pokud považujete zdroj zprostředkovatele typu, vyberte "Důvěřuji tento typ zprostředkovatele." Pokud nedůvěřujete zdroji poskytovatele typu, vyberte "Nedůvěřovat tento typ zprostředkovatele." Důvěřující zprostředkovatel umožňuje spouštět v sadě Visual Studio a na poskytovat technologii IntelliSense, vytváření funkcí. Ale pokud samotného poskytovatele typu se zlými úmysly, spuštěním jeho kódu by mohly ohrozit váš počítač.

Pokud váš projekt obsahuje kód, který odkazuje na zprostředkovateli typů, které jste zvolili v dialogovém okně nedůvěřovat, pak v době kompilace kompilátor ohlásí chybu, která označuje, že zprostředkovatel typu není důvěryhodný. Všechny typy, které jsou závislé na poskytovatele nedůvěryhodné typu jsou označeny červenou vlnovkou. Je bezpečné procházení kódu v editoru.

Pokud se rozhodnete pro provedení změny nastavení vztahu důvěryhodnosti přímo v sadě Visual Studio, proveďte následující kroky.

### <a name="to-change-the-trust-settings-for-type-providers"></a>Chcete-li změnit nastavení vztahu důvěryhodnosti pro zprostředkovatele typů

1. Na `Tools` nabídce vyberte možnost `Options`a rozbalte `F# Tools` uzlu.

2. Vyberte `Type Providers`a v seznamu poskytovatelů typů, zaškrtněte políčko pro důvěryhodného poskytovatele typu a zrušte zaškrtnutí políčka pro ty, kterým nedůvěřujete.

## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé typů](index.md)
