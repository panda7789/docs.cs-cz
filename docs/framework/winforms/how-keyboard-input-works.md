---
title: "Jak funguje vstup z klávesnice"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43b92051b6524a730735fea98d64ee64578b4e06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-keyboard-input-works"></a>Jak funguje vstup z klávesnice
Windows Forms zpracovává vstup z klávesnice ve vyvolání události klávesnice v reakci na zpráv systému Windows. Většina aplikací Windows Forms zpracovat vstup z klávesnice výhradně pomocí zpracování události klávesnice. Nicméně budete muset pochopili, jak funguje zprávy klávesnice, můžete implementovat pokročilejší scénáře vstupu klávesnice, jako je například brání klíče, než dosáhnou ovládacího prvku. Toto téma popisuje typy klíčová data, že Windows Forms rozpozná a poskytuje přehled o tom, jak se směrují klávesnice zprávy. Informace o události klávesnice najdete v tématu [události klávesnice s použitím](../../../docs/framework/winforms/using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Typy klíčů  
 Windows Forms identifikuje vstup z klávesnice jako virtuální klíč kódy, které jsou reprezentované pomocí bitové hodnotě <xref:System.Windows.Forms.Keys> výčtu. Pomocí <xref:System.Windows.Forms.Keys> výčtu, můžete kombinovat řadu stisknuté klávesy za následek jednu hodnotu. Tyto hodnoty odpovídají hodnotám, doprovázejících zprávy WM_KEYDOWN a WM_SYSKEYDOWN Windows. Můžete zjistit většiny fyzických stisknutí klávesy zpracování <xref:System.Windows.Forms.Control.KeyDown> nebo <xref:System.Windows.Forms.Control.KeyUp> události. Znak klíče, jsou podmnožinou <xref:System.Windows.Forms.Keys> výčet a odpovídat na hodnoty doprovázejících zprávy WM_CHAR a WM_SYSCHAR Windows. Pokud kombinace stisknuté klávesy výsledkem znak, můžete zjistit znak zpracování <xref:System.Windows.Forms.Control.KeyPress> událostí. Alternativně můžete použít <xref:Microsoft.VisualBasic.Devices.Keyboard>, zveřejněné programovací rozhraní jazyka Visual Basic, zjišťovat, byly stisknutí klávesy a odesílat klíče. Další informace najdete v tématu [přístup ke klávesnici](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Pořadí událostí klávesnice  
 Jak je uvedeno výše, existují 3 klávesové související události, které se můžou vyskytnout v ovládacím prvku. Následující sekvence zobrazuje obecné pořadí událostí:  
  
1.  Uživatel nabízených oznámení "a" klíč, zpracované klíče, Odeslat a <xref:System.Windows.Forms.Control.KeyDown> dojde k události.  
  
2.  Uživatel má "a" klíč, zpracované klíče, Odeslat a <xref:System.Windows.Forms.Control.KeyPress> dojde k události.  
  
     Jako uživatel obsahuje klíč, dojde k této události vícekrát.  
  
3.  Verze uživatele je zpracované "a" klíč klíče, Odeslat a <xref:System.Windows.Forms.Control.KeyUp> dojde k události.  
  
## <a name="preprocessing-keys"></a>Předběžné zpracování klíče  
 Jako další zprávy zpracování zpráv klávesnice v <xref:System.Windows.Forms.Control.WndProc%2A> metoda formuláře nebo ovládacího prvku. Nicméně před klávesnice zpracování zpráv, <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metoda volá jednu nebo více metod, které může být potlačena za účelem zpracování speciální znak klíčích a fyzické. Můžete přepsat tyto metody ke zjišťování a filtrovat určité klíče, než zprávy zpracuje pomocí ovládacího prvku. Následující tabulka uvádí akce, která provádí a související metody, která je v pořadí, že dojde k metodě.  
  
### <a name="preprocessing-for-a-keydown-event"></a>Předběžné zpracování pro KeyDown – událost  
  
|Akce|Související metody|Poznámky|  
|------------|--------------------|-----------|  
|Zkontrolujte, zda klíč příkaz například akcelerátoru nebo místní nabídky.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Tato metoda zpracovává příkaz klíč, který má přednost před regulární klíče. Pokud tato metoda vrátí hodnotu `true`, klíčová zpráva není odeslat, a klíče události nedojde. Vrátí-li `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> se označuje jako`.`|  
|Kontrolovat speciální klíč, který vyžaduje předběžného zpracování nebo normální znak klíč, který by měla vyvolat <xref:System.Windows.Forms.Control.KeyDown> událostí a odeslán do ovládacího prvku.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Pokud metoda vrátí `true`, znamená to ovládací prvek je znak regulární a <xref:System.Windows.Forms.Control.KeyDown> událost se vyvolá. Pokud `false`, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> je volána. **Poznámka:** aby ovládacího prvku získá klíče nebo kombinace kláves, může zpracovat <xref:System.Windows.Forms.Control.PreviewKeyDown> událostí a sadu <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> z <xref:System.Windows.Forms.PreviewKeyDownEventArgs> k `true` pro klíče nebo klíče, které chcete.|  
|Zkontrolujte, zda klíč navigace (ESC, karta, vraťte se a klávesy se šipkami).|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Tato metoda zpracovává fyzické klíč, který využívá zvláštní funkce v ovládacím prvku, jako je například přepínání mezi ovládacího prvku a jeho nadřazený objekt. Pokud ztratíte kontrolu nad nezpracovává klíč, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> se volá na nadřazeného ovládacího prvku a tak dále do ovládacího prvku nejhornější v hierarchii. Pokud tato metoda vrátí hodnotu `true`, předběžného zpracování je dokončena a nevygenerovala klíče události. Vrátí-li `false`, <xref:System.Windows.Forms.Control.KeyDown> dojde k události.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>Předběžné zpracování pro KeyPress – událost  
  
|Akce|Související metody|Poznámky|  
|------------|--------------------|-----------|  
|Zkontrolujte, že klíč je normální znak, který má být zpracován, ovládacím prvkem|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Pokud znak je znak normální, vrátí tato metoda `true`, <xref:System.Windows.Forms.Control.KeyPress> událost se vyvolá, a dojde k žádné další předběžné zpracování. V opačném případě <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> bude volána.|  
|Zkontrolujte, zda znak je symbol a (například & OK na tlačítku)|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Tato metoda je podobná <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, bude volána hierarchie ovládacího prvku. Pokud ovládací prvek ovládacího prvku kontejneru, vyhledává klávesové zkratky voláním <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> na sebe sama a jeho podřízených ovládacích prvků. Pokud <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> vrátí `true`, <xref:System.Windows.Forms.Control.KeyPress> události nedojde.|  
  
## <a name="processing-keyboard-messages"></a>Zpracování zpráv s klávesnice  
 Po klávesnice zprávy reach <xref:System.Windows.Forms.Control.WndProc%2A> metoda formuláře nebo ovládacího prvku, jsou zpracovávány pomocí sady metod, které je možné přepsat. Každá z těchto metod vrací <xref:System.Boolean> hodnotu udávající, zda zpráva klávesnice zpracován a spotřebovávají ovládacího prvku. Pokud vrátí jednu z metod `true`, pak zpráva považuje za zpracovat a jeho není předán základní nebo nadřazeného ovládacího prvku pro další zpracování. Zpráva, jinak hodnota zůstává ve frontě zpráv a může být zpracována v jiné metody v základní nebo nadřazeného ovládacího prvku. Následující tabulka představuje metody, které zpracování zpráv klávesnice.  
  
|Metoda|Poznámky|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Tato metoda zpracovává všechny zprávy klávesnice, které jsou přijímány <xref:System.Windows.Forms.Control.WndProc%2A> metody ovládacího prvku.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Tato metoda odešle zprávu klávesnice nadřazeného ovládacího prvku. Pokud <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> vrátí `true`, vygenerování žádné klíče události, jinak <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> je volána.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Tato metoda vyvolá <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, a <xref:System.Windows.Forms.Control.KeyUp> události podle potřeby.|  
  
## <a name="overriding-keyboard-methods"></a>Přepsání metody klávesnice  
 Existuje mnoho způsobů přepsání, pokud je zpráva klávesnice zpracované a zpracovat; Některé metody jsou však mnohem lepší možnosti než jiné. Následující tabulka uvádí úlohy, které můžete chtít provést a nejlepší způsob, jak přepsání metody klávesnice. Další informace o přepsání metody naleznete v tématu [přepisování vlastnosti a metody v odvozených třídách](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Úloha|Metoda|  
|----------|------------|  
|Zachytávat navigační klíč a zvýšit <xref:System.Windows.Forms.Control.KeyDown> událostí. Můžete například chtít KARTĚ a vraťte se ke zpracování v textovém poli.|Přepsání <xref:System.Windows.Forms.Control.IsInputKey%2A>. **Poznámka:** Alternativně může zpracovat <xref:System.Windows.Forms.Control.PreviewKeyDown> událostí a sadu <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> z <xref:System.Windows.Forms.PreviewKeyDownEventArgs> k `true` pro klíče nebo klíče, které chcete.|  
|Proveďte zvláštní zpracování vstupu nebo navigační prvku. Například chcete použití klávesy se šipkami ve vašem ovládací prvek seznamu, chcete-li změnit vybrané položky.|Přepsání<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Zachytávat navigační klíč a zvýšit <xref:System.Windows.Forms.Control.KeyPress> událostí. Například v ovládacím prvku číselník budete chtít že klíč k vícenásobné šipku stiskem tlačítka pro urychlení rozšiřování prostřednictvím položky.|Přepsání <xref:System.Windows.Forms.Control.IsInputChar%2A>.|  
|Zvláštní zpracování vstupu nebo navigační během provádění <xref:System.Windows.Forms.Control.KeyPress> událostí. Například v seznamu řízení podržíte stisknutou klávesu "r" mezi položkami, které začínají písmeno r přeskočí.|Přepsání<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|Proveďte vlastní symbolické zpracování; například chcete zpracovávat klávesové zkratky vykreslovaných vlastníkem tlačítek obsažené v panelu nástrojů.|Přepsání <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.WndProc%2A>  
 <xref:System.Windows.Forms.Control.PreProcessMessage%2A>  
 [Objekt My.Computer.Keyboard](~/docs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)  
 [Přístup ke klávesnici](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)  
 [Použití událostí klávesnice](../../../docs/framework/winforms/using-keyboard-events.md)
