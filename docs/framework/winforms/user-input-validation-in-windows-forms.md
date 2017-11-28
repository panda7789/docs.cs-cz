---
title: "Ověřování uživatelského vstupu ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48a28db24731f9aa248bb149c9f19a57cf76bbf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="user-input-validation-in-windows-forms"></a>Ověřování uživatelského vstupu ve Windows Forms
Při zadávání dat do aplikace, můžete ověřit platnost data předtím, než je vaše aplikace používá. Může vyžadovat určité textová pole nesmí být nulová délka, naformátovat pole jako telefonní číslo nebo jiný typ dat ve správném formátu, nebo že řetězec neobsahuje žádné nebezpečné znaky, které by mohly být použity k ohrožení zabezpečení databáze. Windows Forms poskytuje několik způsobů ověření vstupu ve vaší aplikaci.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>Ověření s ovládacím prvkem MaskedTextBox  
 Pokud potřebujete po uživatelích vyžadovat zadání data v dobře definovaný formátu, například telefonní číslo nebo číslo část toho lze dosáhnout rychle a s minimálními kódu pomocí <xref:System.Windows.Forms.MaskedTextBox> ovládacího prvku. A *maska* je řetězec znaky z maskování jazyk, který určuje, které znaky, si můžete zaznamenat na dané pozici v textovém poli. Tento ovládací prvek zobrazí sadu výzvy pro uživatele. Pokud uživatel zadá nesprávnou položku, například uživatel zadá písmeno, pokud je potřeba číslici, ovládacího prvku automaticky odmítnou vstup.  
  
 Maskování jazyk, který je používán <xref:System.Windows.Forms.MaskedTextBox> je velmi flexibilní. Umožňuje vám zadat znaků, volitelné znaků, literálů, pomlčky a kulaté závorky, měny znaků a datum oddělovačů. Ovládací prvek také funguje i při vázání ke zdroji dat. <xref:System.Windows.Forms.Binding.Format> Události u vazby dat slouží k opakovanému formátování příchozích dat pro dosažení souladu s maskou a <xref:System.Windows.Forms.Binding.Parse> událostí slouží k opakovanému formátování odchozích dat k zajištění souladu se specifikacemi pole data.  
  
 Další informace najdete v tématu [MaskedTextBox – ovládací prvek](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Ověřování založeného na událostech  
 Chcete-li úplné programovou kontrolu nad ověření, nebo třeba provést složité ověřovacích kontrol, měli byste použít události ověření součástí většina ovládacích prvků Windows Forms. Má každý ovládací prvek, který přijímá vlastní uživatelský vstup <xref:System.Windows.Forms.Control.Validating> událost, která dojde vždy, když ověření dat vyžaduje ovládací prvek. V <xref:System.Windows.Forms.Control.Validating> metoda zpracování událostí, můžete ověřit uživatelský vstup několika způsoby. Pokud máte textové pole, které musí obsahovat poštovní směrovací číslo, je třeba provést ověření následujícími způsoby:  
  
-   Pokud poštovnímu směrovacímu číslu musí patřit do určité skupiny PSČ, můžete provést porovnání řetězců na vstup ověřit data zadaná uživatelem. Například pokud v sadě {10001, 10002, 10003} musí být zadané PSČ, pak můžete porovnání řetězců ověřit data.  
  
-   Pokud poštovní směrovací číslo musí být v konkrétní formuláře můžete ověřit data zadaná uživatelem regulární výrazy. Například pro ověření formátu `#####` nebo `#####-####`, můžete použít s regulárním výrazem `^(\d{5})(-\d{4})?$`. Ověření formuláře `A#A #A#`, můžete použít s regulárním výrazem `[A-Z]\d[A-Z] \d[A-Z]\d`. Další informace o regulárních výrazech najdete v tématu [regulární výrazy rozhraní .NET Framework](../../../docs/standard/base-types/regular-expressions.md) a [Příklady regulárních výrazů](../../../docs/standard/base-types/regular-expression-examples.md).  
  
-   Pokud zadané PSČ musí být platné PSČ USA, může volání PSČ webové služby ověřit data zadaná uživatelem.  
  
 <xref:System.Windows.Forms.Control.Validating> Událostí je zadaný objekt typu <xref:System.ComponentModel.CancelEventArgs>. Pokud zjistíte, že data ovládacího prvku není platný, můžete zrušit <xref:System.Windows.Forms.Control.Validating> událostí nastavením tohoto objektu <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost `true`. Pokud není nastaveno <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost Windows Forms se předpokládá, že se ověřování bylo úspěšné pro ovládací prvek a vygenerovat <xref:System.Windows.Forms.Control.Validated> událostí.  
  
 Příklad kódu, který ověří e-mailovou adresu v <xref:System.Windows.Controls.TextBox>, najdete v části <xref:System.Windows.Forms.Control.Validating>.  
  
### <a name="data-binding-and-event-driven-validation"></a>Datové vazby a ověřování založeného na událostech  
 Ověření je velmi užitečné, když je ovládací prvek vázán vaše ovládací prvky ke zdroji dat, jako je například databázové tabulky. Pomocí ověřování, můžete zkontrolovat, může nebezpečné dat ovládacího prvku splňuje formátu potřebném zdroj dat, a že není obsahovat žádné speciální znaky, jako je například uvozovek a zpět lomítka.  
  
 Při použití datové vazby dat ve vašem ovládacím prvku je synchronizován se zdrojem dat během provádění <xref:System.Windows.Forms.Control.Validating> událostí. Pokud zrušíte <xref:System.Windows.Forms.Control.Validating> událostí, data nebudou synchronizovat se zdrojem dat.  
  
> [!IMPORTANT]
>  Pokud máte vlastní ověření, který probíhá po <xref:System.Windows.Forms.Control.Validating> událostí, nebude to mít vliv datové vazby. Například, pokud máte kódu <xref:System.Windows.Forms.Control.Validated> událost, která se pokusí zrušit datové vazby, datové vazby přesto dojde. V tomto případě k provedení ověření v <xref:System.Windows.Forms.Control.Validated> událostí, změňte ovládacího prvku **režim aktualizace zdroje dat** vlastnost (**pod (datové vazby)**\\**(rozšířené)** ) z **OnValidation** k **nikdy**a přidejte *řízení*`.DataBindings["`*\<YOURFIELD >*  `"].WriteValue()` ověření kódu.  
  
### <a name="implicit-and-explicit-validation"></a>Implicitní a explicitní ověření  
 Proto když data ovládacího prvku získat ověřit? Toto je až vás jako na vývojáři. Můžete použít implicitním nebo explicitním ověření, v závislosti na potřebách vaší aplikace.  
  
#### <a name="implicit-validation"></a>Implicitní ověření  
 Implicitní ověření přístupu ověří data, protože uživatel zadá ho. Data můžete ověřit, jak dat je zadán v ovládacím prvku načtením klíče, jako jsou v stisknutí tlačítka nebo více běžně vždy, když uživatel provede zaměření pro vstup od jeden ovládací prvek a přesune na další. Tento přístup je užitečné, když chcete udělit uživatelské okamžitou zpětnou vazbu o datech, jak pracují.  
  
 Pokud chcete použít implicitní ověření pro ovládací prvek, je nutné nastavit tuto kontrolu <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> vlastnost `true`. Pokud zrušíte <xref:System.Windows.Forms.Control.Validating> událostí, chování ovládacího prvku se určí na základě co hodnoty, které jste přiřadili <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>. Pokud jste přiřadili <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>, zrušení událost způsobí, že <xref:System.Windows.Forms.Control.Validated> není na dojde k události. Zaměření pro vstup zůstane na aktuální ovládací prvek, dokud uživatel nezmění data na platnou hodnotu. Pokud jste přiřadili <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>, <xref:System.Windows.Forms.Control.Validated> událostí nedojde, pokud zrušíte událost, ale přesto změní fokus na další ovládací prvek.  
  
 Přiřazení <xref:System.Windows.Forms.AutoValidate.Disable> k <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> vlastnost zabraňuje implicitní ověření úplně. Chcete-li ověřit vaše ovládací prvky, budete muset použít explicitní ověření.  
  
#### <a name="explicit-validation"></a>Explicitní ověření  
 Explicitní ověření přístupu ověří data najednou. Můžete ověřit data v reakci na akci uživatele, jako je například kliknutí na tlačítko Uložit nebo odkaz Další. Když dojde k akci uživatele, můžete aktivovat explicitní ověření v jednom z následujících způsobů:  
  
-   Volání <xref:System.Windows.Forms.ContainerControl.Validate%2A> ověření ovládacího prvku poslední ztratil fokus.  
  
-   Volání <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> ověření všech podřízených ovládacích prvků v ovládacím prvku formuláře nebo kontejneru.  
  
-   Volání vlastní metody ověřit data v ovládacích prvcích ručně.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Výchozí chování implicitní ověřování pro Windows Forms – ovládací prvky  
 Různé ovládací prvky Windows Forms mít různé výchozí hodnoty pro jejich <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> vlastnost. Následující tabulka uvádí nejběžnější ovládací prvky a jejich výchozí hodnoty.  
  
|Ovládací prvek|Výchozí chování při ověřování|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Vlastnosti nejsou viditelné v sadě Visual Studio|  
|<xref:System.Windows.Forms.ToolStripContainer>|Vlastnosti nejsou viditelné v sadě Visual Studio|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Zavřením formuláře a přepsáním ověření  
 Když ovládacího prvku udržuje zaměřuje, protože data, která obsahuje je neplatná, není možné zavřít formulář nadřazené obvyklé způsoby:  
  
-   Kliknutím **Zavřít** tlačítko.  
  
-   Výběrem **Zavřít** v **systému** nabídky.  
  
-   Při volání <xref:System.Windows.Forms.Form.Close%2A> metoda prostřednictvím kódu programu.  
  
 Ale v některých případech můžete chtít mohl uživatel zavřete formulář bez ohledu na to, jestli jsou platné hodnoty v ovládacích prvcích. Můžete přepsat ověření a zavřete formulář, který ještě obsahuje neplatná data tak, že vytvoříte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Closing> události. V události, nastavte <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost `false`. Vynutí se tak formulář zavřete. Další informace a příklady naleznete v tématu <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Pokud vynutíte formulář zavřete tímto způsobem, dojde ke ztrátě dat v ovládacích prvcích formuláře, který ještě nebyl uložen. Kromě toho modální forms neověřují obsah ovládacích prvků, když jsou uzavřeny. Můžete použít ovládací prvek ověření přesto k uzamčení fokus na ovládací prvek, ale nemáte starat o chování přidružené zavřením formuláře.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
 <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>  
 [MaskedTextBox – ovládací prvek](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)  
 [Příklady regulárních výrazů](../../../docs/standard/base-types/regular-expression-examples.md)
