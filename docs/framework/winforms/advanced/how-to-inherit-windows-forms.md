---
title: 'Postupy: Dědění v modelu Windows Forms'
ms.date: 03/30/2017
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: 60c238430d44371bbd3859c3864fd2ef73f70098
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037915"
---
# <a name="how-to-inherit-windows-forms"></a>Postupy: Dědění v modelu Windows Forms

Vytváření nových model Windows Forms děděním ze základních formulářů je praktický způsob, jak duplikovat vaše nejlepší úsilí, aniž byste museli projít celým procesem zcela znovu vytvořit formulář pokaždé, když ho budete potřebovat.

Další informace o dědění formulářů v době návrhu pomocí dialogového okna **Výběr dědičnosti** a o tom, jak vizuálně odlišit úrovně zabezpečení u zděděných ovládacích prvků [, naleznete v tématu How to: Dědění formulářů pomocí dialogového okna](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)Výběr dědičnosti.

> [!NOTE]
> Aby bylo možné dědit z formuláře, soubor nebo obor názvů obsahující tento formulář musí být integrovány do spustitelného souboru nebo knihovny DLL. Chcete-li sestavit projekt, v nabídce **sestavení** klikněte na příkaz **sestavit** . Také odkaz na obor názvů musí být přidán do třídy dědění formuláře.

## <a name="inherit-a-form-programmatically"></a>Dědění formuláře prostřednictvím kódu programu

1. Ve třídě přidejte odkaz na obor názvů obsahující formulář, ze kterého chcete dědit.

2. V definici třídy přidejte odkaz na formulář, ze kterého se dědí. Odkaz by měl zahrnovat obor názvů, který obsahuje formulář, následovaný tečkou, potom název základního formuláře samotného.

    ```vb
    Public Class Form2
        Inherits Namespace1.Form1
    ```

    ```csharp
    public class Form2 : Namespace1.Form1
    ```

 Při dědění formulářů Pamatujte na to, že problémy mohou nastat s ohledem na obslužné rutiny událostí, které jsou volány dvakrát, protože každá událost je zpracovávána základní třídou a zděděnou třídou. Další informace o tom, jak se vyhnout tomuto problému, najdete [v tématu řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).

## <a name="see-also"></a>Viz také:

- [Příkaz Inherits](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [Příkaz Imports (obor názvů a typ .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [using](~/docs/csharp/language-reference/keywords/using.md)
- [Účinky úpravy vzhledu základního formuláře](effects-of-modifying-base-form-appearance.md)
- [Vizuální dědění modelu Windows Forms](windows-forms-visual-inheritance.md)
