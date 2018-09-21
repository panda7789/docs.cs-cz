---
title: Chyby v rámci doby návrhu v Návrháři formulářů Windows
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
ms.openlocfilehash: ec1801a1b695867a7edcd99394feebe1d0f6853a
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46490137"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Chyby v rámci doby návrhu v Návrháři formulářů Windows
Toto téma vysvětluje význam a použití seznamu chyb při návrhu, který se zobrazí v sadě Microsoft Visual Studio, když Návrhář formulářů Windows nepodaří načíst. Pokud se zobrazí tento seznam chyb, by neměla interpretovat jako chyba v návrháři, ale jako pomůcka pro opravu chyb v kódu.  
  
 Základní znalosti o tento seznam chyb můžete ladit aplikace tak, že poskytuje podrobné informace o chybách a navrhněte řešení.  
  
## <a name="the-design-time-error-list-interface"></a>Rozhraní seznam chyb při návrhu  
 Pokud se nepodaří načíst Návrháře formulářů Windows, seznamu chyb se zobrazí v návrháři. Chyby jsou seskupené do kategorií. Například pokud máte čtyři instance nedeklarované proměnné, ty budou seskupeny do stejné kategorie chyby. Každá kategorie chyby obsahuje stručný popis, který shrnuje chybu.  
  
 Můžete rozbalit nebo Sbalit kategorii chyby, kliknutím na záhlaví kategorie chyby nebo kliknutím na dvojitou šipku Rozbalit/sbalit. Když rozbalíte kategorii chyby, zobrazí se následující další pomoc:  
  
-   Instance této chyby.  
  
-   Nápověda k této chybě.  
  
-   Fórum příspěvky o této chybě.  
  
### <a name="instances-of-this-error"></a>Instance této chyby  
 Další nápověda seznam všech instancí chybu v aktuálním projektu. Mnoho chyb obsahovat přesné umístění v následujícím formátu: *[název projektu]* *[název formuláře]* řádku:*[číslo]* sloupec:*– sloupec číslo*. **Přejít ke kódu** odkaz vás nasměruje na umístění ve vašem kódu, kde dojde k chybě.  
  
 Pokud zásobníku volání je spojen s chybou, můžete kliknout **zobrazit zásobník volání** propojení, které dále rozšiřujících chyby, chcete-li zobrazit zásobník volání. Zkoumání zásobník může poskytnout cenné informace o ladění. Můžete například sledovat, funkce, které byly volány předtím, než došlo k chybě. Zásobník volání je volitelný, takže můžete zkopírovat a uložit ho.  
  
> [!NOTE]
>  V jazyce Visual Basic v seznamu chyb při návrhu nezobrazí více než jednu chybu, ale může zobrazovat více instancí stejné chybě. Chyby v aplikaci Visual C++, nemají goto code odkazy nebo odkazy na čísla řádku.  
  
### <a name="help-with-this-error"></a>Nápověda k této chybě  
 Pokud chyba obsahuje odkaz na související téma nápovědy MSDN, další pomoc bude obsahovat odkaz na téma nápovědy. Když kliknete na odkaz, zobrazí se v sadě Visual Studio související téma nápovědy.  
  
### <a name="forum-posts-about-this-error"></a>Fórum příspěvky o této chybě  
 Další pomoc, bude obsahovat odkaz na příspěvků na fórech MSDN týkající se chyby. Fóra budou vyhledány podle řetězec chybové zprávy. Můžete také zkusit hledání následující fóra:  
  
-   [Fórum Návrháře formulářů Windows](https://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [Windows Forms fóra](https://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a>Ignorovat a pokračovat  
 Můžete ignorovat chybovou podmínku a pokračovat v načítání návrháře. Výběrem této akce může způsobit neočekávané chování. Například ovládací prvky se nemusí zobrazit na návrhové ploše.  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží s vývojem během návrhu](https://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [Řešení potíží s vytvářením ovládacích prvků a komponent](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 [Vývoj ovládacích prvků Windows Forms v době návrhu](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Chybové zprávy Návrháře formulářů Windows](https://msdn.microsoft.com/library/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
