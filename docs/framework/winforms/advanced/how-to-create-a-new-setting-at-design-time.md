---
title: 'Postupy: Vytvoření nového nastavení při návrhu'
description: Naučte se, jak vytvořit nové nastavení model Windows Forms v době návrhu pomocí návrháře nastavení v aplikaci Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: ce37b42191999e29de2f2f7f7e7abfa0ec3f4d47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325843"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a>Postupy: vytvoření nového nastavení v době návrhu

Nové nastavení můžete vytvořit v době návrhu pomocí návrháře nastavení v aplikaci Visual Studio. Návrhář nastavení je rozhraní ve stylu mřížky, které umožňuje vytvořit nové nastavení a zadat vlastnosti těchto nastavení. Pro nová nastavení musíte zadat název, hodnotu, typ a rozsah. Jakmile je nastavení vytvořeno, je přístupné v kódu.

## <a name="create-a-new-setting-at-design-time-in-c"></a>Vytvořit nové nastavení v době návrhu v jazyce C\#

1. Otevřete sadu Visual Studio.

2. V **Průzkumník řešení**rozbalte uzel **vlastnosti** projektu.

3. Dvakrát klikněte na soubor. Settings, ve kterém chcete přidat nové nastavení. Výchozí název tohoto souboru je Settings. Settings.

4. V Návrháři nastavení nastavte **název**, **hodnotu**, **typ**a **Rozsah** vašeho nastavení. Každý řádek představuje jedno nastavení.

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a>Vytvořit nové nastavení v době návrhu v Visual Basic

1. Otevřete sadu Visual Studio.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**.

3. Na stránce **vlastnosti** vyberte kartu **Nastavení** .

4. V Návrháři nastavení nastavte **název**, **hodnotu**, **typ**a **Rozsah** vašeho nastavení. Každý řádek představuje jedno nastavení.

## <a name="see-also"></a>Viz také

- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Přehled nastavení aplikace](application-settings-overview.md)
- [Postupy: Změna hodnoty existujícího nastavení při návrhu](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
