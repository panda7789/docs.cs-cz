---
title: Jak funguje vstup z klávesnice
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: 369c434f5443334ccb8b136ce50ff2d5db8ece01
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963450"
---
# <a name="how-keyboard-input-works"></a>Jak funguje vstup z klávesnice
Model Windows Forms zpracovává vstup klávesnice tím, že vyvolává události klávesnice v reakci na zprávy systému Windows. Většina model Windows Forms aplikací zpracovává vstup z klávesnice výhradně tím, že zpracovává události klávesnice. Je však třeba pochopit, jak fungují zprávy klávesnice, abyste mohli implementovat pokročilejší scénáře zadávání klávesnice, jako je zachycení klíčů předtím, než dosáhnou ovládacího prvku. Toto téma popisuje typy klíčových dat, která model Windows Forms rozpoznat, a poskytuje přehled o směrování zpráv z klávesnice. Informace o událostech klávesnice najdete v tématu [použití událostí klávesnice](using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Typy klíčů  
 Model Windows Forms identifikuje vstup z klávesnice jako kódy virtuálních klíčů, které jsou reprezentovány <xref:System.Windows.Forms.Keys> bitovým výčtem. Pomocí výčtu <xref:System.Windows.Forms.Keys> můžete kombinovat řadu stisknutých kláves, aby byla výsledkem jediná hodnota. Tyto hodnoty odpovídají hodnotám, které doprovázejí zprávy Windows WM_KEYDOWN a WM_SYSKEYDOWN. Většinu fyzických klíčů můžete zjistit zpracováním <xref:System.Windows.Forms.Control.KeyDown> událostí nebo. <xref:System.Windows.Forms.Control.KeyUp> Znakové klíče jsou podmnožinou <xref:System.Windows.Forms.Keys> výčtu a odpovídají hodnotám, které doprovázejí zprávy systému Windows WM_CHAR a WM_SYSCHAR. Pokud kombinace stisknutých kláves zavede znak, můžete rozpoznat znak tím, že se <xref:System.Windows.Forms.Control.KeyPress> událost zpracuje. Alternativně můžete použít <xref:Microsoft.VisualBasic.Devices.Keyboard>a vystavit Visual Basic programovací rozhraní, abyste zjistili, které klávesy byly stisknuté a odesílané klíče. Další informace najdete v tématu [přístup k klávesnici](../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Pořadí událostí klávesnice  
 Jak je uvedeno výše, existují 3 události související s klávesnicí, ke kterým může dojít na ovládacím prvku. Následující sekvence zobrazuje obecné pořadí událostí:  
  
1. Uživatel přehraje klíč "a", klíč se předzpracováním, odešle a <xref:System.Windows.Forms.Control.KeyDown> dojde k události.  
  
2. Uživatel drží klíč "a", klíč je předzpracovaný, odeslán a <xref:System.Windows.Forms.Control.KeyPress> dojde k události.  
  
     Tato událost nastane víckrát, protože uživatel drží klíč.  
  
3. Uživatel uvolní klíč "a", klíč je předzpracovaný, byl odeslán a <xref:System.Windows.Forms.Control.KeyUp> dojde k události.  
  
## <a name="preprocessing-keys"></a>Klíče předběžného zpracování  
 Podobně jako jiné zprávy jsou zprávy klávesnice zpracovávány v <xref:System.Windows.Forms.Control.WndProc%2A> metodě formuláře nebo ovládacího prvku. Před zpracováním <xref:System.Windows.Forms.Control.PreProcessMessage%2A> zpráv klávesnice však metoda volá jednu nebo více metod, které lze přepsat za účelem zpracování speciálních znakových klíčů a fyzických klíčů. Tyto metody můžete přepsat pro detekci a filtrování určitých klíčů předtím, než je zpráva zpracována ovládacím prvkem. Následující tabulka ukazuje prováděnou akci a související metodu, ke které dojde, v pořadí, ve kterém se metoda vyskytuje.  
  
### <a name="preprocessing-for-a-keydown-event"></a>Předzpracování pro událost KeyDown  
  
|Akce|Související metoda|Poznámky|  
|------------|--------------------|-----------|  
|Vyhledejte příkazový klíč, jako je například akcelerátor nebo zástupce nabídky.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Tato metoda zpracovává klíč příkazu, který má přednost před běžnými klíči. Pokud tato metoda vrátí `true`hodnotu, zpráva Key není odeslána a událost klíče se neobjeví. Pokud se vrátí `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> je volána`.`|  
|Kontrola speciálního klíče, který vyžaduje předzpracování nebo normální klíč znaku, který by měl vyvolat <xref:System.Windows.Forms.Control.KeyDown> událost a být odeslán do ovládacího prvku.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Pokud se metoda vrátí `true`, znamená to, že je ovládací prvek běžným znakem <xref:System.Windows.Forms.Control.KeyDown> a je vyvolána událost. Pokud `false`jevolána. <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> **Poznámka:**  Chcete-li zajistit, že ovládací prvek získá klíč nebo kombinaci klíčů, můžete zpracovat <xref:System.Windows.Forms.Control.PreviewKeyDown> událost a sadu <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> <xref:System.Windows.Forms.PreviewKeyDownEventArgs> `true` pro klíč nebo klíče, které chcete.|  
|Vyhledejte navigační klíč (klávesy ESC, TAB, Return nebo šipky).|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Tato metoda zpracovává fyzický klíč, který využívá speciální funkce v rámci ovládacího prvku, jako je Přepnutí fokusu mezi ovládacím prvkem a jeho nadřazeným prvkem. Pokud přímý ovládací prvek nezpracovává klíč, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> je vyvolána v nadřazeném ovládacím prvku a tak dále k nejvyššímu ovládacímu prvku v hierarchii. Pokud tato metoda vrátí `true`, předzpracování je dokončeno a událost klíče se nevygeneruje. Pokud se vrátí `false` <xref:System.Windows.Forms.Control.KeyDown> , dojde k události.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>Předzpracování pro událost KeyPress  
  
|Akce|Související metoda|Poznámky|  
|------------|--------------------|-----------|  
|Zkontrolujte, zda je klíč normálním znakem, který by měl být zpracován ovládacím prvkem.|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Pokud je znak normálním znakem, vrátí `true`Tato metoda <xref:System.Windows.Forms.Control.KeyPress> , událost je vyvolána a nedojde k žádnému dalšímu předběžnému zpracování. V <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> opačném případě bude volána.|  
|Zkontrolujte, zda je znak symbolický (například & OK na tlačítku).|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Tato metoda, podobně jako <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, bude volána v hierarchii ovládacích prvků. Je-li ovládací prvek kontejner ovládacího prvku, kontroluje, zda jsou volány <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> pomocí sebe sama a jeho podřízených ovládacích prvků. Pokud <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> vrátí `true` ,<xref:System.Windows.Forms.Control.KeyPress> událost neproběhne.|  
  
## <a name="processing-keyboard-messages"></a>Zpracování zpráv klávesnice  
 Po tom, co klávesové <xref:System.Windows.Forms.Control.WndProc%2A> zprávy dosáhnou metody formuláře nebo ovládacího prvku, jsou zpracovány sadou metod, které lze přepsat. Každá z těchto metod vrátí <xref:System.Boolean> hodnotu určující, zda byla zpráva klávesnice zpracována a spotřebována ovládacím prvkem. Pokud se jedna z metod vrátí `true`, je zpráva považována za zpracovanou a není předána základnímu nebo nadřazenému ovládacímu prvku pro další zpracování. V opačném případě zpráva zůstane ve frontě zpráv a může být zpracována jinou metodou v základní nebo nadřazené části ovládacího prvku. Následující tabulka uvádí metody, které zpracovávají zprávy z klávesnice.  
  
|Metoda|Poznámky|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Tato metoda zpracovává všechny zprávy klávesnice, které jsou přijímány <xref:System.Windows.Forms.Control.WndProc%2A> metodou ovládacího prvku.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Tato metoda pošle zprávu klávesnice nadřazenému ovládacímu prvku. Pokud <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> se `true`vrátí, nevygeneruje se žádná klíčová <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> událost, jinak se zavolá.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Tato metoda v případě <xref:System.Windows.Forms.Control.KeyDown>potřeby <xref:System.Windows.Forms.Control.KeyPress>vyvolává události <xref:System.Windows.Forms.Control.KeyUp> , a.|  
  
## <a name="overriding-keyboard-methods"></a>Přepsání metod klávesnice  
 Existuje mnoho metod, které lze přepsat při předzpracování a zpracování zprávy klávesnice; Některé metody jsou však mnohem lepší než jiné. V následující tabulce jsou uvedeny úlohy, které můžete chtít provést, a nejlepší způsob, jak potlačit metody klávesnice. Další informace o přepsání metod naleznete v tématu [přepisování vlastností a metod v odvozených třídách](../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Úloha|Metoda|  
|----------|------------|  
|Zachytit navigační klíč a vyvolat <xref:System.Windows.Forms.Control.KeyDown> událost. Například požadujete, aby byla karta zpracována v textovém poli.|Přepsat <xref:System.Windows.Forms.Control.IsInputKey%2A>. **Poznámka:**  Alternativně můžete zpracovat <xref:System.Windows.Forms.Control.PreviewKeyDown> událost a <xref:System.Windows.Forms.PreviewKeyDownEventArgs> sadu <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> `true` pro klíč nebo klíče, které chcete.|  
|Provedení speciálního zpracování vstupu nebo navigace na ovládacím prvku. Například chcete změnit vybranou položku pomocí kláves se šipkami v ovládacím prvku seznam.|Prioritu<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Zachytit navigační klíč a vyvolat <xref:System.Windows.Forms.Control.KeyPress> událost. Například v ovládacím prvku s číselníkem, který požadujete vícenásobnou klávesovou zkratku pro zrychlení průběhu položek.|Přepsat <xref:System.Windows.Forms.Control.IsInputChar%2A>.|  
|Provedení speciálního zpracování vstupu nebo navigace během <xref:System.Windows.Forms.Control.KeyPress> události. Například v ovládacím prvku seznamu, který uchovává klíč "r", přeskočí položky, které začínají písmenem r.|Prioritu<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|Provádět vlastní zpracování instrukcí; například chcete zpracovat klávesové zkratky na tlačítkách vydaných vlastníkem, která jsou obsažena na panelu nástrojů.|Přepsat <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.WndProc%2A>
- <xref:System.Windows.Forms.Control.PreProcessMessage%2A>
- [Objekt My.Computer.Keyboard](../../visual-basic/language-reference/objects/my-computer-keyboard-object.md)
- [Přístup ke klávesnici](../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)
- [Použití událostí klávesnice](using-keyboard-events.md)
