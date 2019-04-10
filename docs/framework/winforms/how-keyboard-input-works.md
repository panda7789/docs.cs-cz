---
title: Jak funguje vstup z klávesnice
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: ddc2f3338b231ab3ae59e65bc82c00bb8f663540
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342166"
---
# <a name="how-keyboard-input-works"></a>Jak funguje vstup z klávesnice
Windows Forms zpracovává vstup z klávesnice vyvoláním události klávesnice v reakci na Windows zprávy. Většina aplikací Windows Forms zpracovávat vstup z klávesnice výhradně ve zpracování událostí klávesnice. Ale budete muset porozumět fungování zprávy týkající se klávesnice, abyste mohli implementovat pokročilejší scénáře vstup z klávesnice, jako je například zachycení klíče, než dosáhnou ovládacího prvku. Toto téma popisuje typy klíče dat, formulářů Windows rozpoznává a poskytuje přehled o tom, jak se směrují zprávy týkající se klávesnice. Informace o události klávesnice, naleznete v tématu [použití událostí klávesnice](using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Typy klíčů  
 Windows Forms identifikuje vstup z klávesnice jako virtuální klíč kódy, které jsou reprezentovány pomocí bitového <xref:System.Windows.Forms.Keys> výčtu. S <xref:System.Windows.Forms.Keys> výčet, můžete kombinovat řadu při stisknutí klávesy za následek jednu hodnotu. Tyto hodnoty odpovídají hodnotám, které nejsou poskytnuty WM_KEYDOWN a WM_SYSKEYDOWN Windows zprávy. Můžete zjistit většiny fyzických stisknutí kláves zpracování <xref:System.Windows.Forms.Control.KeyDown> nebo <xref:System.Windows.Forms.Control.KeyUp> události. Znaky jsou podmnožinou <xref:System.Windows.Forms.Keys> výčet a odpovídají hodnotám, které nejsou poskytnuty WM_CHAR a WM_SYSCHAR Windows zprávy. Pokud je výsledkem kombinace při stisknutí kláves je znak, můžete zjistit znak zpracování <xref:System.Windows.Forms.Control.KeyPress> událostí. Alternativně můžete použít <xref:Microsoft.VisualBasic.Devices.Keyboard>, vystavené pomocí programovacího rozhraní jazyka Visual Basic, a zjistit, které jsou stisknuty poslat klíči. Další informace najdete v tématu [přístup ke klávesnici](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Řazení událostí klávesnice  
 Jak je uvedeno dříve, existují 3 související události, které se může vyskytnout u ovládacího prvku pomocí klávesnice. Následující sekvence zobrazuje obecné pořadí událostí:  
  
1. Uživatel nabízených oznámení "a" klíč, předzpracovaná klíč odeslána a <xref:System.Windows.Forms.Control.KeyDown> dojde k události.  
  
2. Uživatel obsahuje "a" klíč, předzpracovaná klíč odeslána a <xref:System.Windows.Forms.Control.KeyPress> dojde k události.  
  
     Jako uživatel obsahuje klíč, dojde k této události více než jednou.  
  
3. Odeslat uživatele verze je Předzpracovaný "a" klíč klíč, a <xref:System.Windows.Forms.Control.KeyUp> dojde k události.  
  
## <a name="preprocessing-keys"></a>Předzpracování klíče  
 Stejně jako ostatní zprávy se zpracovávají zprávy týkající se klávesnice v <xref:System.Windows.Forms.Control.WndProc%2A> metody formuláře nebo ovládacího prvku. Nicméně před klávesnice zpracování zpráv, <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metoda volá jeden nebo více metod, které může být potlačena za účelem zpracování speciální znak a fyzické klíče. Můžete přepsat tyto metody pro detekci a filtrování určité klíče předtím, než zprávy zpracuje ovládacím prvkem. Následující tabulka uvádí akce, která se provádí a související metody, ke které dochází, v pořadí, metoda vyvolá.  
  
### <a name="preprocessing-for-a-keydown-event"></a>Předzpracování pro zpracování události KeyDown.  
  
|Akce|Související metody|Poznámky|  
|------------|--------------------|-----------|  
|Vyhledejte klíč příkaz například akcelerátoru nebo zástupce v nabídce.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Tato metoda zpracovává příkaz klíč, který má přednost před regulární klíče. Pokud tato metoda vrátí `true`, není klíčové zpráva odeslána a klíče události nedochází. Vrátí-li `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> nazývá`.`|  
|Kontrolovat speciální klíč, který vyžaduje předběžného zpracování nebo klíč běžný znak, který by měla vyvolat <xref:System.Windows.Forms.Control.KeyDown> událostí a odeslaných do ovládacího prvku.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Pokud metoda vrátí `true`, to znamená, že ovládací prvek je znak regulárního a <xref:System.Windows.Forms.Control.KeyDown> událost se vyvolá. Pokud `false`, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> je volána. **Poznámka:**  Aby ovládací prvek získá klíč nebo kombinace kláves, dokáže zpracovat <xref:System.Windows.Forms.Control.PreviewKeyDown> událostí a nastavte <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> z <xref:System.Windows.Forms.PreviewKeyDownEventArgs> k `true` klíče nebo klíče, které chcete.|  
|Vyhledejte klíč navigace (klávesy ESC, TAB, Return nebo šipka).|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Tato metoda zpracovává fyzické klíč, který využívá speciální funkce v rámci ovládacího prvku, jako je například přepínání mezi ovládacím prvkem a jeho nadřazený objekt. Pokud ztratíte kontrolu nad klíči, nezpracovává <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> je volán na nadřazený ovládací prvek a tak dále do ovládacího prvku nejvyšší v hierarchii. Pokud tato metoda vrátí `true`předběžného zpracování je kompletní a klíče události se nevygeneroval. Vrátí-li `false`, <xref:System.Windows.Forms.Control.KeyDown> dojde k události.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>Předzpracování pro zpracování události KeyPress.  
  
|Akce|Související metody|Poznámky|  
|------------|--------------------|-----------|  
|Zaškrtněte, pokud chcete vidět, že klíč je běžný znak, který má být zpracován ovládacím prvkem|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Pokud je znak, který běžný znak, vrátí tato metoda `true`, <xref:System.Windows.Forms.Control.KeyPress> událost se vyvolá a žádné další předběžné zpracování proběhne. V opačném případě <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> , zavolá se.|  
|Zaškrtněte, pokud chcete zjistit, zda znak je symbol (například & OK na tlačítko)|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Tato metoda je podobný <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, zavolá se hierarchii ovládacího prvku. Pokud je ovládací prvek ovládacího prvku kontejneru, kontrole klávesových zkratek voláním <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> na sebe sama a jeho podřízených ovládacích prvků. Pokud <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> vrátí `true`, <xref:System.Windows.Forms.Control.KeyPress> události nedochází.|  
  
## <a name="processing-keyboard-messages"></a>Zpracování zprávy týkající se klávesnice  
 Po klávesnice zprávy dosahu <xref:System.Windows.Forms.Control.WndProc%2A> metody formuláře nebo ovládacího prvku, se zpracovávají podle sadu metod, které mohou být přepsána nastaveními. Každá z těchto metod vrací <xref:System.Boolean> hodnotu určující, zda zpráva klávesnice zpracování a používané ovládací prvek. Pokud některou z metod vrátí `true`, pak zprávy se považuje za zpracování a není předaný do základní nebo nadřazeného ovládacího prvku pro další zpracování. V opačném případě zpráva zůstane ve frontě zpráv a mohou být zpracovány v jinou metodu v základní nebo nadřazeného ovládacího prvku. Následující tabulka představuje metody, které zpracovávají zprávy týkající se klávesnice.  
  
|Metoda|Poznámky|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Tato metoda zpracovává všechny zprávy týkající se klávesnice, které dostávají <xref:System.Windows.Forms.Control.WndProc%2A> metody ovládacího prvku.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Tato metoda odesílá zprávy klávesnice do nadřazeného ovládacího prvku. Pokud <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> vrátí `true`, není-li generována žádná událost klíče, jinak <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> je volána.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Tato metoda vyvolá <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, a <xref:System.Windows.Forms.Control.KeyUp> události podle potřeby.|  
  
## <a name="overriding-keyboard-methods"></a>Přepsání metody klávesnice  
 Nejsou k dispozici pro přepsání při zprávu klávesnice předzpracovaná a zpracuje; mnoho metod Některé metody jsou však mnohem lepší možnosti než jiné. Následující tabulka uvádí úlohy, které můžete chtít provést a nejlepší způsob, jak přepsat metody klávesnice. Další informace o přepsání metody, naleznete v tématu [přepsání vlastnostem a metodám v odvozených třídách](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Úloha|Metoda|  
|----------|------------|  
|Zachytit klíč navigace a zvýšit <xref:System.Windows.Forms.Control.KeyDown> událostí. Můžete například chtít kartu a vraťte se ke zpracování v textovém poli.|Přepsat <xref:System.Windows.Forms.Control.IsInputKey%2A>. **Poznámka:**  Alternativně můžete zpracovávat <xref:System.Windows.Forms.Control.PreviewKeyDown> událostí a nastavte <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> z <xref:System.Windows.Forms.PreviewKeyDownEventArgs> k `true` klíče nebo klíče, které chcete.|  
|Proveďte zvláštní zpracování vstupu nebo navigaci v ovládacím prvku. Například kterou chcete použít klávesy se šipkami v ovládacím prvku seznamu změnit vybrané položky.|přepsání <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Zachytit klíč navigace a zvýšit <xref:System.Windows.Forms.Control.KeyPress> událostí. V ovládacím prvku číselník – můžete například chtít, že klíč k vícenásobné šipku stiskne ke zrychlení průběh prostřednictvím položky.|Přepsat <xref:System.Windows.Forms.Control.IsInputChar%2A>.|  
|Speciální zpracování vstupu nebo navigace během provádění <xref:System.Windows.Forms.Control.KeyPress> událostí. V seznamu se například ovládací prvek, podržte klávesu "r" přeskočí mezi položkami, které začínají písmenem r.|přepsání <xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|Provést vlastní symbol manipulace; například chcete zpracovávat klávesových zkratek vykreslovaných vlastníkem tlačítek obsažených v panelu nástrojů.|Přepsat <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.WndProc%2A>
- <xref:System.Windows.Forms.Control.PreProcessMessage%2A>
- [My.Computer.Keyboard – objekt](~/docs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)
- [Přístup ke klávesnici](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)
- [Použití událostí klávesnice](using-keyboard-events.md)
