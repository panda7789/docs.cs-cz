---
title: Ověření vstupu uživatele
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: eafbf54552566011fef9d2dbeb5e9f9fa3facabd
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646305"
---
# <a name="user-input-validation-in-windows-forms"></a>Ověřování uživatelského vstupu ve Windows Forms
Když uživatelé zadají data do vaší aplikace, můžete ověřit, že data jsou platná před aplikací používá. Můžete požadovat, aby určitá textová pole neměla nulovou délku, aby pole bylo formátováno jako telefonní číslo nebo jiný typ dobře formátovaných dat nebo aby řetězec neobsahoval žádné nebezpečné znaky, které by mohly být použity k ohrožení zabezpečení databáze. Windows Forms poskytuje několik způsobů, jak ověřit vstup ve vaší aplikaci.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>Ověření pomocí ovládacího prvku MaskedTextBox  
 Pokud potřebujete vyžadovat, aby uživatelé zadali data v dobře definovaném formátu, například telefonní číslo nebo číslo <xref:System.Windows.Forms.MaskedTextBox> dílu, můžete to provést rychle a s minimálním kódem pomocí ovládacího prvku. *Maska* je řetězec tvořený znaky z maskovacího jazyka, který určuje, které znaky lze zadat na libovolné pozici v textovém poli. Ovládací prvek zobrazí sadu výzev pro uživatele. Pokud uživatel zadá nesprávnou položku, například uživatel zadá písmeno, když je požadována číslice, ovládací prvek automaticky odmítne vstup.  
  
 Maskovací jazyk, který <xref:System.Windows.Forms.MaskedTextBox> používá, je velmi flexibilní. Umožňuje zadat požadované znaky, volitelné znaky, literálové znaky, například spojovníky a závorky, znaky měny a oddělovače kalendářních dat. Ovládací prvek také funguje dobře, když je vázán na zdroj dat. Událost <xref:System.Windows.Forms.Binding.Format> na datové vazbě lze přeformátovat příchozí data tak, aby <xref:System.Windows.Forms.Binding.Parse> vyhovovala masce, a událost může být použita k přeformátování odchozích dat tak, aby vyhovovala specifikacím datového pole.  
  
 Další informace naleznete v tématu [MaskedTextBox Control](./controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Ověřování řízené událostmi  
 Pokud chcete úplnou programovou kontrolu nad ověřováním nebo potřebujete provést komplexní kontroly ověření, měli byste použít události ověření integrované do většiny ovládacích prvků windows forms. Každý ovládací prvek, který přijímá vstup <xref:System.Windows.Forms.Control.Validating> uživatele volného tvaru, má událost, která nastane vždy, když ovládací prvek vyžaduje ověření dat. V <xref:System.Windows.Forms.Control.Validating> metodě zpracování událostí můžete ověřit vstup uživatele několika způsoby. Máte-li například textové pole, které musí obsahovat PSČ, můžete ověření provést následujícími způsoby:  
  
- Pokud psč musí patřit do určité skupiny PSČ, můžete provést porovnání řetězců na vstupu k ověření dat zadaných uživatelem. Pokud například psČ musí být v sadě {10001, 10002, 10003}, můžete k ověření dat použít porovnání řetězců.  
  
- Pokud musí být PSČ v určitém formuláři, můžete použít regulární výrazy k ověření dat zadaných uživatelem. Chcete-li například `#####` ověřit `#####-####`formulář nebo , `^(\d{5})(-\d{4})?$`můžete použít regulární výraz . Chcete-li `A#A #A#`formulář ověřit , můžete `[A-Z]\d[A-Z] \d[A-Z]\d`použít regulární výraz . Další informace o regulárních výrazech naleznete [v tématu .NET Framework Regular Expressions](../../standard/base-types/regular-expressions.md) and [Regular Expression Examples](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md).  
  
- Pokud psč musí být platné PSČ, můžete zavolat webovou službu PSČ k ověření dat zadaných uživatelem.  
  
 Událost <xref:System.Windows.Forms.Control.Validating> je zadána objekt <xref:System.ComponentModel.CancelEventArgs>typu . Pokud zjistíte, že data ovládacího prvku nejsou <xref:System.Windows.Forms.Control.Validating> platná, můžete událost <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> zrušit `true`nastavením vlastnosti tohoto objektu na . Pokud vlastnost nenastavíte, <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> systém Windows Forms bude předpokládat, že <xref:System.Windows.Forms.Control.Validated> ověření proběhlo pro tento ovládací prvek a vyvolalo událost.  
  
 Příklad kódu, který ověřuje <xref:System.Windows.Controls.TextBox>e-mailovou adresu v oblasti , naleznete v tématu <xref:System.Windows.Forms.Control.Validating>.  
  
### <a name="data-binding-and-event-driven-validation"></a>Ověřování na vazbě dat a událostech  
 Ověření je velmi užitečné, pokud jste svázali ovládací prvky ke zdroji dat, jako je například tabulka databáze. Pomocí ověření se můžete ujistit, že data ovládacího prvku splňuje formát požadovaný zdrojem dat a že neobsahuje žádné speciální znaky, jako jsou uvozovky a zpětná lomítka, která by mohla být nebezpečná.  
  
 Při použití datové vazby jsou data v ovládacím prvku synchronizována se zdrojem dat během provádění <xref:System.Windows.Forms.Control.Validating> události. Pokud <xref:System.Windows.Forms.Control.Validating> událost zrušíte, data nebudou synchronizována se zdrojem dat.  
  
> [!IMPORTANT]
> Pokud máte vlastní ověření, které <xref:System.Windows.Forms.Control.Validating> probíhá po události, nebude mít vliv na datové vazby. Například pokud máte kód <xref:System.Windows.Forms.Control.Validated> v případě, že se pokusí zrušit datovou vazbu, bude stále dojít k datové vazby. V takovém případě chcete-li <xref:System.Windows.Forms.Control.Validated> provést ověření v události, změňte vlastnost **režimu aktualizace zdroje dat** ovládacího prvku (**v části (Datové vazby)**\\ **(Upřesnit)** z **OnValidation na** **Never**a přidejte>`"].WriteValue()` *ovládacího prvku*`.DataBindings["`*\<YOURFIELD* do ověřovacího kódu.  
  
### <a name="implicit-and-explicit-validation"></a>Implicitní a explicitní ověření  
 Takže kdy se data ovládacího prvku ověří? To je na vás, developer. Můžete použít implicitní nebo explicitní ověření, v závislosti na potřebách vaší aplikace.  
  
#### <a name="implicit-validation"></a>Implicitní ověření  
 Implicitní ověřovací přístup ověřuje data, jak je uživatel zadá. Můžete ověřit data jako data zadávají do ovládacího prvku čtením kláves, jak jsou stisknuty, nebo častěji vždy, když uživatel vezme vstupní fokus od jednoho ovládacího prvku a přesune na další. Tento přístup je užitečný, pokud chcete poskytnout uživateli okamžitou zpětnou vazbu o datech při jejich práci.  
  
 Pokud chcete použít implicitní ověření ovládacího prvku, musíte <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> nastavit <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>vlastnost tohoto ovládacího prvku na nebo . Pokud <xref:System.Windows.Forms.Control.Validating> událost zrušíte, bude chování ovládacího prvku určeno jakou <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>hodnotou, kterou jste přiřadili . Pokud jste <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>událost přiřadili <xref:System.Windows.Forms.Control.Validated> , dojde k tomu, že k události nedojde. Vstupní fokus zůstane na aktuálníovládací prvek, dokud uživatel změní data na platný vstup. Pokud jste <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>událost <xref:System.Windows.Forms.Control.Validated> při zrušení události nenastala , ale fokus se stále změní na další ovládací prvek.  
  
 Přiřazení <xref:System.Windows.Forms.AutoValidate.Disable> vlastnosti <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> zabrání implicitní ověření úplně. Chcete-li ověřit ovládací prvky, budete muset použít explicitní ověření.  
  
#### <a name="explicit-validation"></a>Explicitní ověření  
 Explicitní ověřovací přístup ověřuje data najednou. Data můžete ověřit v reakci na akci uživatele, například klepnutí na tlačítko Uložit nebo odkaz Další. Dojde-li k akci uživatele, můžete aktivovat explicitní ověření jedním z následujících způsobů:  
  
- Volání <xref:System.Windows.Forms.ContainerControl.Validate%2A> k ověření posledního ovládacího prvku, který ztratil fokus.  
  
- Volání <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> k ověření všech podřízených ovládacích prvků ve formuláři nebo ovládacím prvku kontejneru.  
  
- Volání vlastní metodu k ověření dat v ovládacích prvcích ručně.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Výchozí chování implicitníověření pro ovládací prvky formulářů systému Windows  
 Různé ovládací prvky Windows Forms <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> mají různé výchozí hodnoty pro jejich vlastnost. V následující tabulce jsou uvedeny nejběžnější ovládací prvky a jejich výchozí hodnoty.  
  
|Řízení|Výchozí chování ověření|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Vlastnost, která není vystavena v sadě Visual Studio|  
|<xref:System.Windows.Forms.ToolStripContainer>|Vlastnost, která není vystavena v sadě Visual Studio|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Zavření formuláře a přepsání ověření  
 Pokud ovládací prvek udržuje fokus, protože data, která obsahuje, jsou neplatná, není možné zavřít nadřazený formulář jedním z obvyklých způsobů:  
  
- Kliknutím na tlačítko **Zavřít.**  
  
- Výběrem **zavřít** v nabídce **Systém.**  
  
- Programovým <xref:System.Windows.Forms.Form.Close%2A> voláním metody.  
  
 V některých případech však můžete chtít nechat uživatele zavřít formulář bez ohledu na to, zda jsou hodnoty v ovládacích prvcích platné. Ověření můžete přepsat a zavřít formulář, který stále obsahuje neplatná data, vytvořením obslužné rutiny pro <xref:System.Windows.Forms.Form.FormClosing> událost formuláře. V případě, nastavte <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost `false`. To vynutí zavření formuláře. Další informace a příklad <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>naleznete v tématu .  
  
> [!NOTE]
> Pokud vynutíte zavření formuláře tímto způsobem, budou ztracena všechna data v ovládacích prvcích formuláře, která ještě nebyla uložena. Kromě toho modální formuláře neověřují obsah ovládacích prvků, když jsou uzavřeny. Ověření ovládacího prvku můžete stále použít k uzamčení fokusu ovládacího prvku, ale nemusíte se obávat chování spojeného s zavřením formuláře.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [MaskedTextBox – ovládací prvek](./controls/maskedtextbox-control-windows-forms.md)
- [Příklady regulárních výrazů](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)
