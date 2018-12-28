---
title: Zabezpečení zprostředkovatele typů
description: Další informace o zabezpečení zprostředkovatele typů v F#, jak změnit nastavení vztahu důvěryhodnosti pro poskytovatele typu.
ms.date: 05/16/2016
ms.openlocfilehash: 9ccb33d7298736c3d6b54980b6fe09bc9f2e0259
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611188"
---
# <a name="type-provider-security"></a>Zabezpečení zprostředkovatele typů

Poskytovatelé typů jsou sestavení (knihovny DLL) odkazuje váš F# project nebo script, které obsahují kód k připojení k externím zdrojům dat a poskytování těchto informací typu F# typu prostředí. Obvykle kód v odkazovaných sestaveních je spustit pouze při kompilaci a následné provádění kódu (nebo v případě skript, odeslat kód, který F# interaktivní). Sestavení zprostředkovatele typu však bude fungovat v sadě Visual Studio při procházení kódu pouze v editoru. K tomu dochází, protože typ poskytovatele potřebné ke přidat dodatečné informace k editoru, jako je například popisky rychlé informace, dokončování IntelliSense a tak dále. V důsledku toho některé další bezpečnostní aspekty pro typ sestavení zprostředkovatele, protože jejich automaticky spuštěn uvnitř procesu Visual Studio.

## <a name="security-warning-dialog"></a>Dialogové okno upozornění zabezpečení

Při prvním použití sestavení zprostředkovatele na určitý typ, Visual Studio zobrazí dialogové okno zabezpečení, která vás upozorní, že zprostředkovatel typu je spuštěn. Před Visual Studio načte typ zprostředkovatele, dává možnost rozhodnout, zda důvěřovat tohoto konkrétního zprostředkovatele. Pokud považujete zdroj zprostředkovatele typu, vyberte "Důvěřuji tento typ zprostředkovatele." Pokud nedůvěřujete zdroji poskytovatele typu, vyberte "Nedůvěřovat tento typ zprostředkovatele." Důvěřující zprostředkovatel umožňuje spouštět v sadě Visual Studio a na poskytovat technologii IntelliSense, vytváření funkcí. Ale pokud samotného poskytovatele typu se zlými úmysly, spuštěním jeho kódu by mohly ohrozit váš počítač.

Pokud váš projekt obsahuje kód, který odkazuje na zprostředkovateli typů, které jste zvolili v dialogovém okně nedůvěřovat, pak v době kompilace kompilátor ohlásí chybu, která označuje, že zprostředkovatel typu není důvěryhodný. Všechny typy, které jsou závislé na poskytovatele nedůvěryhodné typu jsou označeny červenou vlnovkou. Je bezpečné procházení kódu v editoru.

Pokud se rozhodnete pro provedení změny nastavení vztahu důvěryhodnosti přímo v sadě Visual Studio, proveďte následující kroky.

### <a name="to-change-the-trust-settings-for-type-providers"></a>Chcete-li změnit nastavení vztahu důvěryhodnosti pro zprostředkovatele typů

1. Na `Tools` nabídce vyberte možnost `Options`a rozbalte `F# Tools` uzlu.

2. Vyberte `Type Providers`a v seznamu poskytovatelů typů, zaškrtněte políčko pro důvěryhodného poskytovatele typu a zrušte zaškrtnutí políčka pro ty, kterým nedůvěřujete.

## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé typů](index.md)