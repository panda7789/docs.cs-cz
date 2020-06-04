---
title: RaiseEvent – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: 46b93c060a12d82b34dafdf3aa4ea677df6f54cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404288"
---
# <a name="raiseevent-statement"></a>RaiseEvent – příkaz
Aktivuje událost deklarovanou na úrovni modulu v rámci třídy, formuláře nebo dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Součásti  
 `eventname`  
 Povinná hodnota. Název události, která se má aktivovat  
  
 `argumentlist`  
 Nepovinný parametr. Seznam proměnných, polí nebo výrazů oddělených čárkami. `argumentlist`Argument musí být uzavřený v závorkách. Pokud neexistují žádné argumenty, musí být uvozovky vynechány.  
  
## <a name="remarks"></a>Poznámky  
 Požadovaná `eventname` je název události deklarované v rámci modulu. Postupuje podle Visual Basic konvence pojmenovávání proměnných.  
  
 Pokud událost nebyla deklarována v modulu, ve kterém je vyvolána, dojde k chybě. Následující fragment kódu ukazuje deklaraci události a proceduru, ve které je událost vyvolána.  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 Nemůžete použít `RaiseEvent` k vyvolání událostí, které nejsou explicitně deklarovány v modulu. Například všechny formuláře dědí <xref:System.Windows.Forms.Control.Click> událost z <xref:System.Windows.Forms.Form?displayProperty=nameWithType> , nelze je vyvolat pomocí `RaiseEvent` odvozeného formuláře. Pokud deklarujete `Click` událost v modulu formuláře, vystínuje se vlastní <xref:System.Windows.Forms.Control.Click> událost formuláře. Můžete přesto vyvolat <xref:System.Windows.Forms.Control.Click> událost formuláře voláním <xref:System.Windows.Forms.Control.OnClick%2A> metody.  
  
 Ve výchozím nastavení událost definovaná v Visual Basic vyvolává obslužné rutiny událostí v pořadí, ve kterém jsou navázána připojení. Vzhledem k tomu, že události mohou mít `ByRef` parametry, proces, který spojuje pozdě, může přijímat parametry, které byly změněny předchozí obslužnou rutinou události. Po provedení obslužné rutiny události je ovládací prvek vrácen do subrutiny, která událost vyvolala.  
  
> [!NOTE]
> Nesdílené události by neměly být vyvolány v rámci konstruktoru třídy, ve které jsou deklarovány. I když takové události nezpůsobí chyby v době běhu, nemusí se podařit zachytit pomocí přidružených obslužných rutin událostí. Použijte `Shared` modifikátor pro vytvoření sdílené události, pokud potřebujete vyvolat událost z konstruktoru.  
  
> [!NOTE]
> Můžete změnit výchozí chování událostí definováním vlastní události. Pro vlastní události `RaiseEvent` Vyvolá příkaz přístup k události `RaiseEvent` . Další informace o vlastních událostech naleznete v tématu [příkaz Event](event-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá události pro počítání sekund od 10 do 0. Kód znázorňuje několik metod, vlastností a příkazů souvisejících s událostmi, včetně `RaiseEvent` příkazu.  
  
 Třída, která vyvolá událost, je zdrojem události a metody, které zpracovávají události, jsou obslužné rutiny událostí. Zdroj události může mít několik obslužných rutin pro události, které generuje. Když třída vyvolá událost, tato událost je vyvolána na každé třídě, která se rozhodla zpracovávat události pro tuto instanci objektu.  
  
 V příkladu se používá také formulář ( `Form1` ) s tlačítkem ( `Button1` ) a textovým polem ( `TextBox1` ). Když kliknete na tlačítko, zobrazí se v prvním textovém poli odpočítávání od 10 do 0 sekund. Když uplyne celý čas (10 sekund), zobrazí se v prvním textovém poli "Hotovo".  
  
 Kód pro `Form1` Určuje počáteční a koncovou stavy formuláře. Obsahuje také kód spuštěný při vyvolání události.  
  
 Chcete-li použít tento příklad, otevřete nový projekt aplikace pro systém Windows, přidejte tlačítko s názvem `Button1` a textové pole s názvem `TextBox1` do hlavního formuláře s názvem `Form1` . Potom klikněte pravým tlačítkem myši na formulář a kliknutím na **Zobrazit kód** otevřete Editor kódu.  
  
 Přidejte `WithEvents` proměnnou do oddílu deklarace `Form1` třídy.  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>Příklad  
 Přidejte následující kód do kódu pro `Form1` . Nahraďte všechny duplicitní procedury, které mohou existovat, například `Form_Load` nebo `Button_Click` .  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Stisknutím klávesy F5 spusťte předchozí příklad a klikněte na tlačítko s názvem **Spustit**. V prvním textovém poli se začne počítat sekundy. Když uplyne celý čas (10 sekund), zobrazí se v prvním textovém poli "Hotovo".  
  
> [!NOTE]
> `My.Application.DoEvents`Metoda nezpracovává události přesně stejným způsobem jako formulář. Chcete-li, aby formulář mohl zpracovávat události přímo, můžete použít multithreading. Další informace najdete v tématu [spravovaná vlákna](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Viz také

- [Události](../../programming-guide/language-features/events/index.md)
- [Event – příkaz](event-statement.md)
- [AddHandler – příkaz](addhandler-statement.md)
- [RemoveHandler – příkaz](removehandler-statement.md)
- [Handles](handles-clause.md)
