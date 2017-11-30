---
title: "Chyby v rámci doby návrhu v Návrháři formulářů Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 819b624e2abac09aea804311d661f78e2a1f5a7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Chyby v rámci doby návrhu v Návrháři formulářů Windows
Toto téma vysvětluje význam a používání seznamu chyb návrhu, které se zobrazí v sadě Microsoft Visual Studio po Návrhář formulářů Windows nepodaří načíst. Pokud se zobrazí tento seznam chyb, by neměl interpretovat jako chyby v návrháři, ale jako pomůcku při opravách chyb v kódu.  
  
 Základní znalosti o tento seznam chyb můžete ladit aplikace tak, že poskytuje podrobné informace o chybách a návrhy možná řešení.  
  
## <a name="the-design-time-error-list-interface"></a>Rozhraní seznamu Chyba v době návrhu  
 Pokud návrhář formulářů Windows se nepodaří načíst, Chyba při seznamu se zobrazí v návrháři. Chyby jsou seskupené do kategorií. Například pokud máte čtyři instancí nedeklarované proměnných, tyto budou seskupeny do stejné kategorie chyby. Každá kategorie chyby zahrnuje stručný popis, který shrnuje chyba.  
  
 Můžete rozbalit nebo sbalit chyba kategorie, buď kliknutím na záhlaví kategorie chyby nebo kliknutím na dvojitou šipku Rozbalit/sbalit. Pokud rozbalíte kategorii chyby, zobrazí se následující další nápovědu:  
  
-   Instance této chyby.  
  
-   Nápověda k této chybě.  
  
-   Fórum odešle o této chybě.  
  
### <a name="instances-of-this-error"></a>Instance této chyby  
 Další nápověda seznam všech instancí chybu v aktuálním projektu. Mnoho chyb zahrnují přesné umístění v následujícím formátu: *[název projektu]* *[název formuláře]* řádku:*[číslo řádku]* sloupce:*[číslo sloupce]*. **Přejít ke kódu** odkazu přejdete do umístění ve vašem kódu, kde dojde k chybě.  
  
 Pokud zásobníku volání je přidružen k chybě, můžete kliknout **zobrazit zásobníkem volání** odkaz, který rozbalí další chyby zobrazíte zásobníku volání. Zkoumání zásobníku může poskytnout cenné informace o ladění. Například můžete sledovat funkce, které bylo voláno před se stala chyba. V zásobníku volání je volitelný, takže můžete zkopírovat a uložit ho.  
  
> [!NOTE]
>  V jazyce Visual Basic v seznamu chyb návrhu nezobrazí více než jednu chybu, ale může zobrazovat více instancí ke stejné chybě. Chyby v jazyce Visual C++, nemají goto kód odkazy nebo čáry číslo odkazy.  
  
### <a name="help-with-this-error"></a>Nápověda k této chybě  
 Pokud chyba obsahuje odkaz související téma nápovědy MSDN, potřebujete další pomoc obsahují odkaz na téma nápovědy. Když kliknete na odkaz, zobrazí se v sadě Visual Studio přidružené téma nápovědy.  
  
### <a name="forum-posts-about-this-error"></a>Fórum příspěvky o této chybě  
 Potřebujete další pomoc, bude obsahovat odkaz na MSDN příspěvcích týkající se chyby. Ve fórech vyhledávají podle řetězec chybové zprávy. Můžete také zkusit vyhledávání fórech o následující:  
  
-   [Návrhář fórum pro Windows Forms](http://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [Windows Forms fóra](http://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a>Ignorovat a pokračovat  
 Můžete chybu ignorovat a pokračovat v načítání návrháře. Výběr tato akce může vést k neočekávanému chování. Například ovládací prvky nacházet na návrhovou plochu.  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží s vývoj návrhu](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [Řešení potíží s komponenty vytváření a řízení](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 [Vývoj Windows Forms – ovládací prvky v době návrhu](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Windows Forms návrháře chybové zprávy](http://msdn.microsoft.com/en-us/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
