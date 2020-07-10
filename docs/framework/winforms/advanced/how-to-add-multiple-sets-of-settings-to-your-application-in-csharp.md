---
title: 'Postupy: Přidání více množin nastavení do vaší aplikace v C#'
description: Naučte se, jak do aplikace v jazyce C# přidat více sad model Windows Forms nastavení pomocí sady Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 579374ff101758b3224bc122c46b891280ed2609
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173442"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Postupy: Přidání více sad nastavení do aplikace v jazyce C\#

V některých případech možná budete chtít mít v aplikaci více sad nastavení. Například při vývoji aplikace, kde se očekává, že se určitá skupina nastavení často mění, může být vhodné je rozdělit do jediného souboru, aby bylo možné tento soubor nahradit, takže ostatní nastavení neovlivní. Sada Visual Studio umožňuje přidat do projektu více sad nastavení. K dalším sadám nastavení lze přistupovat prostřednictvím `Properties.Settings` objektu.

## <a name="add-an-additional-set-of-settings"></a>Přidat další sadu nastavení

1. V aplikaci Visual Studio v nabídce **projekt** vyberte možnost **Přidat novou položku**.

   Otevře se dialogové okno **Přidat novou položku** .

2. V dialogovém okně **Přidat novou položku** vyberte možnost **soubor nastavení**, zadejte název souboru a kliknutím na tlačítko **Přidat** přidejte nový soubor nastavení do řešení.

3. V **Průzkumník řešení**přetáhněte nový soubor nastavení do složky Properties ( **vlastnosti** ). To umožňuje, aby vaše nová nastavení byla k dispozici v kódu.

4. V tomto souboru můžete přidat a použít nastavení stejným způsobem jako jakýkoli jiný soubor nastavení. K této skupině nastavení můžete přistupovat prostřednictvím `Properties.Settings` objektu.

## <a name="see-also"></a>Viz také

- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Přehled nastavení aplikace](application-settings-overview.md)
