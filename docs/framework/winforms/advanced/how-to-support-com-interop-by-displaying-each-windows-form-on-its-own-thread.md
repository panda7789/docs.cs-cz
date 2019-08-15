---
title: 'Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně'
ms.date: 03/30/2017
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 90bbd7df45424f8513598e9d7439d8ae6bf6f52c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040308"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně

Problémy s interoperabilitou modelu COM můžete vyřešit zobrazením formuláře ve smyčce zprávy .NET Framework, kterou lze vytvořit pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.

Chcete-li, aby formulář Windows pracoval správně z klientské aplikace modelu COM, je nutné spustit formulář ve smyčce model Windows Forms zpráv. K tomu použijte jeden z následujících přístupů:

- K zobrazení formuláře Windows použijte metodu.<xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Další informace najdete v tématu [jak: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody](com-interop-by-displaying-a-windows-form-shadow.md)ShowDialog.

- Zobrazí každý formulář Windows v samostatném vlákně.

Existuje Rozsáhlá podpora pro tuto funkci v aplikaci Visual Studio.

Viz [také návod: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))vlastním vlákně.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak zobrazit formulář v samostatném vlákně a volat <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metodu pro spuštění model Windows Formsho pumpy zpráv v tomto vlákně. Chcete-li použít tento přístup, je nutné zařadit všechna volání do formuláře z nespravované aplikace pomocí <xref:System.Windows.Forms.Control.Invoke%2A> metody.

Tento přístup vyžaduje, aby každá instance formuláře běžela ve vlastním vlákně pomocí vlastní smyčky zpráv. V jednom vlákně nemůžete mít spuštěnou více než jednu smyčku zpráv. Proto nemůžete změnit smyčku zpráv klientské aplikace. Můžete však upravit komponentu .NET Framework a spustit nové vlákno, které používá vlastní smyčku zpráv.

[!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]

[!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]

[!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]

## <a name="compile-the-code"></a>Kompilace kódu

Zkompilujte typy `COMForm`, `Form1`a `FormManager` do sestavení s názvem `COMWinform.dll`. Zaregistrujte sestavení pro zprostředkovatele komunikace s objekty COM pomocí jedné z metod popsaných v tématu [sbalení sestavení pro model COM](../../interop/packaging-an-assembly-for-com.md). Nyní můžete použít sestavení a jeho odpovídající soubor knihovny typů (. tlb) v nespravovaných aplikacích. Například můžete použít knihovnu typů jako referenci v spustitelném projektu Visual Basic 6,0.

## <a name="see-also"></a>Viz také:

- [Vystavení komponent architektury .NET Framework pro COM](../../interop/exposing-dotnet-components-to-com.md)
- [Zabalení sestavení pro model COM](../../interop/packaging-an-assembly-for-com.md)
- [Registrování sestav pomocí modelu COM](../../interop/registering-assemblies-with-com.md)
- [Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md)
- [Přehled modelu Windows Forms a nespravovaných aplikací](windows-forms-and-unmanaged-applications-overview.md)
