---
title: Automatický výběr formátu
ms.date: 03/30/2017
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
ms.openlocfilehash: 9b9b4da4d5d3bdb3892feb49c033fbe4fc640cb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="automatic-format-selection"></a>Automatický výběr formátu
Tento příklad ukazuje, jak povolit automatický výběr formátu (XML nebo JSON) se zbytkem Windows Communication Foundation (WCF) programovací model, jakož i explicitně nastavení formátu v kód operace.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Ukázkový soubor obsahuje službu společně s kód klienta, který slouží k žádosti o službu. Služba podporuje jeden HTTP `GET` operace (`EchoWithGet`) a jeden HTTP `POST` operace (`EchoWithPost`). Obě operace očekávat řetězec a pak se vraťte řetězec v odpovědi. Pomocí `GET` operace, řetězec je zadaný parametr řetězce dotazu identifikátoru URI. Pomocí `POST` operace, řetězec je k dispozici v textu požadavku na serializovanou ve formátu XML. Služba se bude moct vrátit odpovědi v XML nebo JSON, využívá nové automatický výběr formátu a imperativní formát výběru funkcí [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
 V ukázce je povolen automatický výběr formátu pomocí souboru App.config. Na výchozí koncový bod webové HTTP `automaticFormatSelectionEnabled` atribut nebyla zadána hodnota `true`. S automatický výběr formátu povoleno [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury vybere nejvhodnější formát odpovědi (XML nebo JSON) zadané přijmout HTTP nebo Content-Type hlavičky žádosti. Vývojář není potřeba zadat další kód nebo konfigurace než nastavení `automaticFormatSelectionEnabled` atribut `true` k použití této funkce. Kód klienta v souboru Program.cs požadavky se odešlou do obou `GET` a `POST` operace služby s hlavičku HTTP přijmout zadaný jako "application/xml" nebo "application/json" a služby v tom, že vrátí odpověď příslušné formát.  
  
 Také v `GET` operace, imperativní formát výběru se používá. `GET` Operace zjišťuje volitelný `format` parametr s řetězcem dotazu a pokud je k dispozici, nastaví formát odpovědi <xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A> vlastnost. Imperativní nastavení formát odpovědi tímto způsobem přepsání automatický výběr formátu provádí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury.  
  
 Ukázkový soubor obsahuje služba s vlastním hostováním a klienta, který běží v konzolové aplikaci. Konzolové aplikace běží, klient odešle žádosti o službu a zapisuje příslušné informace z odpovědi do okna konzoly.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení pro automatické vzorovou výběr formátu. Při spouštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], musíte spustit jako správce pro vzorovou proběhl úspěšně. To můžete provést kliknutím pravým tlačítkem myši [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonu a vyberte **spustit jako správce** v místní nabídce.  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B sestavte řešení a potom stiskněte klávesu Ctrl + F5 a spusťte projekt konzolové aplikace AutomaticFormatSelection. V okně konzoly se zobrazí a poskytuje identifikátor URI spuštěné služby a identifikátor URI HTML stránka pro spuštěnou službu nápovědy.  
  
3.  Ukázka běží, klient odešle požadavky do služby a zapíše odpovědi do okna konzoly. Všimněte si různých formátech odpovědí v XML a JSON.  
  
4.  Stisknutím libovolné klávesy ukončit vzorku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## <a name="see-also"></a>Viz také
