---
title: Ověřování uživatelského vstupu ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: c8a40706df4274728b438cff2539173a0e94b767
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800123"
---
# <a name="user-input-validation-in-windows-forms"></a>Ověřování uživatelského vstupu ve Windows Forms
Pokud uživatel zadá data do vaší aplikace, můžete chtít ověřit, že data nejsou platná předtím, než je vaše aplikace používá. Může vyžadovat určité textová pole nesmí být nulové délky, naformátovat pole jako telefonní číslo nebo jiný typ dat ve správném formátu, nebo zda řetězec neobsahuje všechny problematické znaky, které může ohrozit zabezpečení databáze. Windows Forms poskytuje několik způsobů, jak si můžete ověřit vstup ve vaší aplikaci.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>Ověření s ovládacím prvkem MaskedTextBox  
 Pokud potřebujete budou muset uživatelé zadat data v podrobně definovaném formátu, jako je například telefonní číslo nebo číslo části toho lze dosáhnout rychle a s minimem kódu s použitím <xref:System.Windows.Forms.MaskedTextBox> ovládacího prvku. A *maska* se řetězec skládá ze znaků z maskování jazyk, který určuje, jaké znaky můžete zadat na dané pozici v textovém poli. Ovládací prvek zobrazuje sadu výzvy uživateli. Pokud uživatel zadá nesprávné položky, například uživatel zadá písmeno, když se vyžaduje číslici, ovládací prvek automaticky odmítne vstupu.  
  
 Maskování jazyk, ve kterém je používán <xref:System.Windows.Forms.MaskedTextBox> je velmi flexibilní. Umožňuje zadat požadované znaky, volitelné znaky, literály, například pomlčky a závorky, měny znaky a oddělovače data. I když svázán se zdrojem dat funguje také ovládací prvek. <xref:System.Windows.Forms.Binding.Format> Událostí o datové vazbě je možné opakovaně formátovat příchozích dat k zajištění souladu s maskou a <xref:System.Windows.Forms.Binding.Parse> události je možné změnit formát odchozích dat k zajištění souladu se specifikací datové pole.  
  
 Další informace najdete v tématu [MaskedTextBox – ovládací prvek](./controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Ověřování založené na událostech  
 Pokud chcete úplné programový kontrolu nad ověření nebo potřeba provádět složité ověřovacích kontrol, měli byste použít události ověření integrované do většiny ovládacích prvků Windows Forms. Každý ovládací prvek, který přijímá vstup uživatele volného tvaru <xref:System.Windows.Forms.Control.Validating> události, ke které dojde pokaždé, když se vyžaduje ověření dat ovládací prvek. V <xref:System.Windows.Forms.Control.Validating> metody zpracování událostí, můžete ověřit uživatelský vstup několika způsoby. Pokud máte textové pole, které musí obsahovat poštovní směrovací číslo, je třeba provést ověření následujícími způsoby:  
  
- Pokud PSČ musí patřit do specifické skupiny aplikace PSČ, můžete provést porovnání řetězců na vstupu se ověřit data zadaná uživatelem. Například pokud v sadě {10001, 10002, 10003} musí být poštovní směrovací číslo místa, pak můžete použít porovnání řetězců ověřit data.  
  
- Pokud poštovní směrovací číslo musí být ve formě konkrétní můžete ověřit data zadaná uživatelem regulární výrazy. Například pro ověření formuláře `#####` nebo `#####-####`, můžete použít regulární výraz `^(\d{5})(-\d{4})?$`. Ověření formuláře `A#A #A#`, můžete použít regulární výraz `[A-Z]\d[A-Z] \d[A-Z]\d`. Další informace o formátování regulárních výrazů, naleznete v tématu [regulárních výrazech .NET Frameworku](../../standard/base-types/regular-expressions.md) a [Příklady regulárních výrazů](../../standard/base-types/regular-expression-examples.md).  
  
- Pokud poštovní směrovací číslo musí být platné PSČ USA, lze volat PSČ webovou službu, která ověřit data zadaná uživatelem.  
  
 <xref:System.Windows.Forms.Control.Validating> Událostí je poskytnut objekt typu <xref:System.ComponentModel.CancelEventArgs>. Pokud zjistíte, že data ovládacího prvku není platný, můžete je zrušit <xref:System.Windows.Forms.Control.Validating> události tak, že nastavíte tento objekt <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost `true`. Pokud nenastavíte <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost, Windows Forms bude předpokládat, že ověření proběhlo úspěšně pro tento ovládací prvek a zvýšit <xref:System.Windows.Forms.Control.Validated> událostí.  
  
 Příklad kódu, který ověřuje e-mailovou adresu v <xref:System.Windows.Controls.TextBox>, naleznete v tématu <xref:System.Windows.Forms.Control.Validating>.  
  
### <a name="data-binding-and-event-driven-validation"></a>Vytváření datových vazeb a ověřování založené na událostech  
 Ověření je velmi užitečné, když své ovládací prvky mají vazba ke zdroji dat, jako jsou databázové tabulky. Pomocí ověřování, abyste měli jistotu, že data ovládacího prvku splňuje formátu potřebném ve zdroji dat, a, že ho neobsahuje žádné speciální znaky, jako je například uvozovky a zpět lomítka, která může nebezpečné.  
  
 Při použití datových vazeb dat v ovládacím prvku synchronizována se zdrojem dat během provádění <xref:System.Windows.Forms.Control.Validating> událostí. V případě zrušení <xref:System.Windows.Forms.Control.Validating> událostí, data se nebudou synchronizovat se zdrojem dat.  
  
> [!IMPORTANT]
>  Pokud máte vlastní ověřování, které u něho po <xref:System.Windows.Forms.Control.Validating> událostí, nebude to mít vliv datové vazby. Například, pokud máte kódu <xref:System.Windows.Forms.Control.Validated> událost, která se pokusí zrušit vazbu dat, datové vazby přesto dojde. V tomto případě k provedení ověření v <xref:System.Windows.Forms.Control.Validated> události, Změna ovládacího prvku **režim aktualizace zdroje dat** vlastnosti (**pod (Databindings)**\\ **(rozšířené)** ) z **OnValidation** k **nikdy**a přidejte *ovládací prvek*`.DataBindings["`*\<YOURFIELD >*  `"].WriteValue()` ověření kódu.  
  
### <a name="implicit-and-explicit-validation"></a>Implicitní a explicitní ověřování  
 Proto když data ovládacího prvku ověřovat? Toto je jenom na vás, vývojář. Můžete použít implicitní nebo explicitní ověření, v závislosti na potřebách vaší aplikace.  
  
#### <a name="implicit-validation"></a>Implicitní ověření  
 Implicitní ověření přístupu ověří data jako uživatel zadá ho. Data můžete ověřit, jak data je zadán v ovládacího prvku pomocí čtení klíče, jako jsou stisknutí nebo více běžně pokaždé, když uživatel má vstupní fokus z jednoho ovládacího prvku a přesune na další. Tento přístup je užitečný, pokud chcete poskytnout okamžitou zpětnou vazbu uživatelů o datech, jak pracují.  
  
 Pokud chcete použít implicitní ověření pro ovládací prvek, je nutné nastavit tento ovládací prvek <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> vlastnost `true`. V případě zrušení <xref:System.Windows.Forms.Control.Validating> události, chování ovládacího prvku určí co hodnoty, které jste přiřadili <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>. Pokud jste přiřadili <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>, zrušení události způsobí, že <xref:System.Windows.Forms.Control.Validated> není na výskyt události. Zaměření pro vstup zůstanou v aktuální ovládací prvek, dokud se uživatel nezmění data na platný vstup. Pokud jste přiřadili <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>, <xref:System.Windows.Forms.Control.Validated> události nevyvolá při zrušení události, ale na další ovládací prvek bude stále změnit fokus.  
  
 Přiřazení <xref:System.Windows.Forms.AutoValidate.Disable> k <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> vlastnost zabraňuje implicitním ověření úplně se vynechá. Pokud chcete ověřit své ovládací prvky, budete muset použít explicitní ověřování.  
  
#### <a name="explicit-validation"></a>Explicitní ověřování  
 Explicitní ověření přístupu ověří data najednou. Můžete ověřit data v reakci na akci uživatele, jako je kliknutí na tlačítko Uložit nebo odkaz Další. Pokud dojde k akci uživatele, můžete aktivovat explicitní ověřování v jednom z následujících způsobů:  
  
- Volání <xref:System.Windows.Forms.ContainerControl.Validate%2A> ověření poslední ovládací prvek ztratil fokus.  
  
- Volání <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> ověření všech podřízených ovládacích prvků v ovládacím prvku formulář nebo kontejneru.  
  
- Volání vlastní metody ověření dat v ovládacích prvcích ručně.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Výchozí chování implicitní ověřování pro Windows Forms ovládací prvky  
 Různé ovládací prvky Windows Forms mít různé výchozí hodnoty pro jejich <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> vlastnost. V následující tabulce jsou uvedeny nejčastěji používané ovládací prvky a jejich výchozí hodnoty.  
  
|Control|Výchozí chování ověřování|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Vlastnost není vystaveno v sadě Visual Studio|  
|<xref:System.Windows.Forms.ToolStripContainer>|Vlastnost není vystaveno v sadě Visual Studio|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Zavřením formuláře a přepsání ověření  
 Když ovládacího prvku udržuje fokus, protože je neplatná data, která obsahuje, není možné nadřazený formulář zavřete obvyklé způsoby:  
  
- Kliknutím **Zavřít** tlačítko.  
  
- Výběrem **Zavřít** v **systému** nabídky.  
  
- Při volání <xref:System.Windows.Forms.Form.Close%2A> metoda prostřednictvím kódu programu.  
  
 Nicméně v některých případech můžete chtít uživatelům povolit, bez ohledu na to, zda jsou platné hodnoty v ovládacích prvcích formulář zavřete. Můžete přepsat ověření a zavřete formulář, který se stále obsahuje neplatná data tak, že vytvoříte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Closing> událostí. V případě nastavení <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost `false`. To přinutí formulář zavřete. Další informace a příklad najdete v tématu <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Pokud vynutíte formulář zavřete tímto způsobem, dojde ke ztrátě dat v ovládacích prvcích ve formuláři, která dosud nebyla uložena. Modální formuláře navíc neověřují obsah ovládacích prvků, když jsou uzavřeny. Ovládací prvek ověření můžete stále použít k uzamčení fokus na ovládací prvek, ale nemusíte mít obavy o chování asociovaných s zavřením formuláře.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>
- <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>
- [Ovládací prvek MaskedTextBox](./controls/maskedtextbox-control-windows-forms.md)
- [Příklady regulárních výrazů](../../standard/base-types/regular-expression-examples.md)
