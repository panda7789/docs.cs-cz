---
title: Ověřování uživatelského vstupu ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: 2b83e94f188f46d0cedc9fed9e9c5a946ada59c5
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960430"
---
# <a name="user-input-validation-in-windows-forms"></a>Ověřování uživatelského vstupu ve Windows Forms
Když uživatelé zadávají do aplikace data, možná budete chtít ověřit, že jsou data platná, než je aplikace použije. Můžete vyžadovat, aby určitá textová pole nebyla nulová, aby pole bylo formátováno jako telefonní číslo nebo jiný typ dat ve správném formátu, nebo aby řetězec neobsahoval žádné nezabezpečené znaky, které by bylo možné použít k ohrožení zabezpečení databáze. Model Windows Forms poskytuje několik způsobů, jak ověřit vstup ve vaší aplikaci.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>Ověřování pomocí ovládacího prvku ovládacím MaskedTextBox  
 Pokud potřebujete, aby uživatelé zadali data v dobře definovaném formátu, jako je telefonní číslo nebo číslo součásti, můžete to rychle a s minimálním kódem pomocí ovládacího prvku <xref:System.Windows.Forms.MaskedTextBox>. *Maska* je řetězec tvořený znaky z maskující jazyk, který určuje, které znaky lze zadat v libovolné pozici v textovém poli. Ovládací prvek zobrazí sadu výzev pro uživatele. Pokud uživatel zadá nesprávnou položku, například uživatel zadá písmeno, pokud je požadována číslice, ovládací prvek automaticky zamítne vstup.  
  
 Jazyk maskování, který používá <xref:System.Windows.Forms.MaskedTextBox>, je velmi flexibilní. Umožňuje zadat požadované znaky, volitelné znaky, literálové znaky, například spojovníky a závorky, znaky měny a oddělovače dat. Ovládací prvek také funguje dobře, pokud je svázán se zdrojem dat. Událost <xref:System.Windows.Forms.Binding.Format> v datové vazbě se dá použít k přeformátování příchozích dat tak, aby odpovídala masce, a událost <xref:System.Windows.Forms.Binding.Parse> se dá použít k přeformátování odchozích dat tak, aby splňovala specifikace datového pole.  
  
 Další informace naleznete v tématu [ovládacím MaskedTextBox Control](./controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Ověřování založené na událostech  
 Pokud chcete úplnou programovou kontrolu nad ověřením nebo potřebujete provést komplexní kontroly ověřování, měli byste použít události ověřování integrované do většiny model Windows Formsch ovládacích prvků. Každý ovládací prvek, který přijímá vstup uživatele volné formy, má <xref:System.Windows.Forms.Control.Validating> událost, ke které dojde pokaždé, když ovládací prvek vyžaduje ověření dat. V metodě zpracování událostí <xref:System.Windows.Forms.Control.Validating> můžete ověřit vstup uživatele několika způsoby. Například pokud máte textové pole, které musí obsahovat poštovní směrovací číslo, můžete provést ověřování následujícími způsoby:  
  
- Pokud poštovní směrovací číslo musí patřit do konkrétní skupiny PSČ, můžete provést porovnání řetězců u vstupu a ověřit data zadaná uživatelem. Pokud například poštovní směrovací číslo musí být v sadě {10001, 10002, 10003}, můžete použít porovnání řetězců k ověření dat.  
  
- Pokud poštovní směrovací číslo musí být v konkrétním formuláři, můžete použít regulární výrazy k ověření dat zadaných uživatelem. Chcete-li například ověřit, `#####` nebo `#####-####`formuláře, můžete použít regulární výraz `^(\d{5})(-\d{4})?$`. Chcete-li ověřit `A#A #A#`formuláře, můžete použít regulární výraz `[A-Z]\d[A-Z] \d[A-Z]\d`. Další informace o regulárních výrazech naleznete v tématu [.NET Framework regulární výrazy](../../standard/base-types/regular-expressions.md) a [Příklady regulárních výrazů](../../standard/base-types/regular-expression-examples.md).  
  
- Pokud poštovní směrovací číslo musí být platným USA PSČ, mohli byste zavolat webovou službu ZIP Code k ověření dat zadaných uživatelem.  
  
 Událost <xref:System.Windows.Forms.Control.Validating> je poskytována objektem typu <xref:System.ComponentModel.CancelEventArgs>. Pokud určíte, že data ovládacího prvku nejsou platná, můžete událost <xref:System.Windows.Forms.Control.Validating> zrušit nastavením vlastnosti <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> tohoto objektu na `true`. Pokud vlastnost <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> nenastavíte, model Windows Forms bude předpokládat, že ověření pro daný ovládací prvek proběhlo úspěšně, a vyvolat událost <xref:System.Windows.Forms.Control.Validated>.  
  
 Příklad kódu, který ověřuje e-mailovou adresu v <xref:System.Windows.Controls.TextBox>, najdete v tématu <xref:System.Windows.Forms.Control.Validating>.  
  
### <a name="data-binding-and-event-driven-validation"></a>Vázání dat a ověřování založené na událostech  
 Ověřování je velmi užitečné, pokud jste ovládací prvky navázány na zdroj dat, například databázovou tabulku. Pomocí ověřování se můžete ujistit, že data ovládacího prvku vyhovují formátu požadovanému zdrojem dat a že neobsahuje žádné speciální znaky, jako jsou například uvozovky a zpětná lomítka, která mohou být nebezpečná.  
  
 Když použijete datovou vazbu, data v ovládacím prvku budou synchronizována se zdrojem dat během provádění události <xref:System.Windows.Forms.Control.Validating>. Pokud zrušíte událost <xref:System.Windows.Forms.Control.Validating>, data nebudou synchronizovaná se zdrojem dat.  
  
> [!IMPORTANT]
> Pokud máte vlastní ověření, které proběhne po <xref:System.Windows.Forms.Control.Validating> události, nebude to mít vliv na datovou vazbu. Například pokud máte kód v události <xref:System.Windows.Forms.Control.Validated>, která se pokusí zrušit datovou vazbu, bude stále k dispozici datová vazba. V takovém případě k provedení ověření v události <xref:System.Windows.Forms.Control.Validated> změňte vlastnost **režim aktualizace zdroje dat** ovládacího prvku (**v části (datové vazby)** \\ **(rozšířené)** ) z možnosti- **platnosti** na **nikdy**a přidejte *ovládací prvek*`.DataBindings["` *\<YOURFIELD >* `"].WriteValue()` k ověřovacímu kódu.  
  
### <a name="implicit-and-explicit-validation"></a>Implicitní a explicitní ověřování  
 Takže když se data ovládacího prvku ověřují? To je u vás vývojářem. V závislosti na potřebách vaší aplikace můžete použít buď implicitní, nebo explicitní ověřování.  
  
#### <a name="implicit-validation"></a>Implicitní ověřování  
 Přístup implicitního ověřování ověří data, jakmile je uživatel zadá. Data můžete ověřit při zadávání dat do ovládacího prvku tak, že je přečtete při stisknutí klávesy nebo častěji, kdykoli uživatel převezme fokus vstupu z jednoho ovládacího prvku a přejde na další. Tento přístup je užitečný, když chcete uživateli poskytnout okamžitou zpětnou vazbu k datům při jejich práci.  
  
 Chcete-li pro ovládací prvek použít implicitní ověřování, je nutné nastavit vlastnost <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> tohoto ovládacího prvku na hodnotu <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> nebo <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>. Pokud zrušíte událost <xref:System.Windows.Forms.Control.Validating>, chování ovládacího prvku bude určeno podle hodnoty, kterou jste přiřadili <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>. Pokud jste přiřadili <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>, zrušení události způsobí, že nedojde k události <xref:System.Windows.Forms.Control.Validated>. Vstupní fokus zůstane na aktuálním ovládacím prvku, dokud uživatel nezmění data na platný vstup. Pokud jste přiřadili <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>, událost <xref:System.Windows.Forms.Control.Validated> se při zrušení události neobjeví, ale fokus se stále změní na další ovládací prvek.  
  
 Přiřazení <xref:System.Windows.Forms.AutoValidate.Disable> k vlastnosti <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> znemožňuje implicitní ověřování zcela. Chcete-li ověřit ovládací prvky, budete muset použít explicitní ověřování.  
  
#### <a name="explicit-validation"></a>Explicitní ověření  
 Přístup explicitního ověřování ověřuje data najednou. Můžete ověřit data v reakci na akci uživatele, například kliknutím na tlačítko Uložit nebo na další odkaz. Když dojde k akci uživatele, můžete spustit explicitní ověřování jedním z následujících způsobů:  
  
- Voláním <xref:System.Windows.Forms.ContainerControl.Validate%2A> ověříte, že poslední ovládací prvek ztratil fokus.  
  
- Zavolejte <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> pro ověření všech podřízených ovládacích prvků ve formuláři nebo v ovládacím prvku kontejneru.  
  
- Zavolejte vlastní metodu pro ověření dat v ovládacích prvcích ručně.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Výchozí implicitní chování ověřování pro model Windows Forms ovládací prvky  
 Různé ovládací prvky model Windows Forms mají pro svou vlastnost <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> různé výchozí hodnoty. Následující tabulka uvádí nejběžnější ovládací prvky a jejich výchozí nastavení.  
  
|Control|Výchozí chování ověřování|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Vlastnost není vystavena v aplikaci Visual Studio.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Vlastnost není vystavena v aplikaci Visual Studio.|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Zavření formuláře a přepsání ověřování  
 Když ovládací prvek zachová fokus, protože data, která obsahuje, nejsou platná, není možné zavřít nadřazený formulář jedním z obvyklých způsobů:  
  
- Kliknutím na tlačítko **Zavřít** .  
  
- Výběrem možnosti **Zavřít** v **systémové** nabídce.  
  
- Voláním metody <xref:System.Windows.Forms.Form.Close%2A> programově.  
  
 V některých případech však můžete chtít uživateli nechat formulář zavřít bez ohledu na to, zda jsou hodnoty v ovládacích prvcích platné. Můžete přepsat ověřování a zavřít formulář, který stále obsahuje neplatná data, vytvořením obslužné rutiny pro událost <xref:System.Windows.Forms.Form.FormClosing> formuláře. V takovém případě vlastnost <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> nastavte na hodnotu `false`. Tím se formulář vynutí zavřít. Další informace a příklad najdete v tématu <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>.  
  
> [!NOTE]
> Pokud vynutíte zavření formuláře tímto způsobem, ztratí se všechna data v ovládacích prvcích formuláře, které ještě nebyly uloženy. Kromě toho modální formuláře neověřují obsah ovládacích prvků, když jsou zavřeny. K uzamknutí fokusu na ovládací prvek můžete stále používat ověřování ovládacího prvku, ale nemusíte mít obavy o chování spojené s zavřením formuláře.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [Ovládací prvek MaskedTextBox](./controls/maskedtextbox-control-windows-forms.md)
- [Příklady regulárních výrazů](../../standard/base-types/regular-expression-examples.md)
