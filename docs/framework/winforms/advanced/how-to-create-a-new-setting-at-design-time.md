---
title: 'Postupy: Vytvoření nového nastavení při návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 35a7cd8cc1daaf76a25977751ddc9ec0709e5947
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037908"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a>Postupy: Vytvořit nové nastavení v době návrhu

Nové nastavení můžete vytvořit v době návrhu pomocí návrháře nastavení v aplikaci Visual Studio. Návrhář nastavení je rozhraní ve stylu mřížky, které umožňuje vytvořit nové nastavení a zadat vlastnosti těchto nastavení. Pro nová nastavení musíte zadat název, hodnotu, typ a rozsah. Jakmile je nastavení vytvořeno, je přístupné v kódu.

## <a name="create-a-new-setting-at-design-time-in-c"></a>Vytvořit nové nastavení v době návrhu v jazyce C\#

1. Otevřít Visual Studio.

2. V **Průzkumník řešení**rozbalte uzel **vlastnosti** projektu.

3. Dvakrát klikněte na soubor. Settings, ve kterém chcete přidat nové nastavení. Výchozí název tohoto souboru je Settings. Settings.

4. V Návrháři nastavení nastavte **název**, **hodnotu**, **typ**a **Rozsah** vašeho nastavení. Každý řádek představuje jedno nastavení.

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a>Vytvořit nové nastavení v době návrhu v Visual Basic

1. Otevřít Visual Studio.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**.

3. Na stránce **vlastnosti** vyberte kartu **Nastavení** .

4. V Návrháři nastavení nastavte **název**, **hodnotu**, **typ**a **Rozsah** vašeho nastavení. Každý řádek představuje jedno nastavení.

## <a name="see-also"></a>Viz také:

- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Přehled nastavení aplikace](application-settings-overview.md)
- [Postupy: Změna hodnoty existujícího nastavení v době návrhu](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
