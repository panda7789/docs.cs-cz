---
title: Přehled komponenty PrintDialog
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728677"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog – přehled komponenty (Windows Forms)

Komponenta model Windows Forms [PrintDialog](printdialog-component-windows-forms.md) je předem nakonfigurovaným dialogovým oknem použitým k výběru tiskárny, výběru stránek k tisku a určení dalších nastavení souvisejících s tiskem v aplikacích založených na systému Windows. Použijte ji jako jednoduché řešení pro výběr nastavení tiskárny a tisku místo konfigurace vlastního dialogového okna. Uživatelům můžete umožnit tisk mnoha částí jejich dokumentů: tisknout vše, vytisknout vybraný rozsah stránky nebo vytisknout výběr. Když se spoléháte na standardní dialogová okna systému Windows, vytvoříte aplikace, jejichž základní funkce je pro uživatele okamžitě známa. Komponenta <xref:System.Windows.Forms.PrintDialog> dědí z <xref:System.Windows.Forms.CommonDialog> třídy.

## <a name="working-with-the-component"></a>Práce s komponentou

Použijte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> k zobrazení dialogového okna v době běhu. Tato součást obsahuje vlastnosti, které se vztahují buď na jednu tiskovou úlohu (<xref:System.Drawing.Printing.PrintDocument> třídy), nebo na nastavení jednotlivých tiskáren (<xref:System.Drawing.Printing.PrinterSettings> třídy). Jedna z těchto z nich může být sdílena několika tiskárnami.

Při přidání do formuláře se komponenta <xref:System.Windows.Forms.PrintDialog> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.PrintDialog>
- [Komponenta PrintDialog](printdialog-component-windows-forms.md)
