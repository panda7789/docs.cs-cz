---
title: "Rozšířený výběr formátu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b14aa97f1483b3c69bfecfa0b625e590c0c37836
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="advanced-format-selection"></a>Rozšířený výběr formátu
Tento příklad ukazuje, jak rozšířit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] programovací model REST pro podporu nových odchozí odpovědi formátů. Kromě toho Ukázka používá šablony T4 k vrácení odpovědi jako stránku XHTML ukázka, jak se dají implementovat programovací model styl zobrazení.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Ukázkový soubor obsahuje jednoduché služby společně s kód klienta, který slouží k žádosti o službu.  Služba podporuje jedné operace [WebGet], který má označení následující metody:`Message EchoListWithGet(string list);`  
  
 Když klient odešle požadavek na službu, poskytuje seznam položek z textový soubor s oddělovači `list` parametr s řetězcem dotazu a službu vrátí tento stejný seznam v jednom z následujících formátů: XML, JSON, Atom, XHTML nebo jpeg.  
  
 Služba vrátila formát odpovědi je nejdřív dáno `format` parametr s řetězcem dotazu a sekundu, které hlavičku HTTP přijmout zadaný v požadavku. Pokud hodnota `format` parametr s řetězcem dotazu je jedním z předchozí formátů a pak odpověď se vrátí v tomto formátu. Pokud `format` řetězec dotazu není k dispozici, pak službu iteruje prvky hlavičky Accept z požadavku a vrátí formát první obsahu – typ, který podporuje službu.  
  
 Návratový typ operace je vhodné poznamenat. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Jenom nativně programovací model REST podporuje formáty XML a JSON odpovědi při operace vrátí typ, jiné než <xref:System.ServiceModel.Channels.Message>. Ale při použití <xref:System.ServiceModel.Channels.Message> jako návratový typ vývojář má plnou kontrolu nad formátování obsah zprávy.  
  
 Ukázce se používá <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>, <xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> a <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> metody k serializaci seznam řetězců do XML, JSON a ATOM zpráv v uvedeném pořadí. Pro formát odpovědi jpeg <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> metoda se používá a je obrázek uložen do datového proudu. Pro odpověď v kódu XHTML <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> se používá spolu s předběžně zpracované T4 šablonu, která se skládá z soubor .tt a .cs automaticky generovaný soubor. Soubor .tt umožňuje vývojáři k zápisu odpovědi v podobě šablony, který obsahuje proměnné a řízení struktury. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]T4, najdete v části [generování artefaktů podle pomocí textových šablon](http://go.microsoft.com/fwlink/?LinkId=166023).  
  
 Ukázkový soubor obsahuje služba s vlastním hostováním a klienta, který běží v konzolové aplikaci. Konzolové aplikace běží, klient odešle žádosti o službu a zapisuje příslušné informace z odpovědi do okna konzoly.  
  
#### <a name="to-run-this-sample"></a>Chcete tuto ukázku spustit  
  
1.  Otevřete řešení pro ukázku rozšířené výběr formátu. Při spouštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], byste měli spustit jako správce pro vzorovou proběhl úspěšně. To můžete provést kliknutím pravým tlačítkem myši [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonu a výběr **spustit jako správce** v místní nabídce.  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B sestavte řešení a potom stiskněte klávesu Ctrl + F5 spusťte projekt konzolové aplikace AdvancedFormatSelection bez ladění. V okně konzoly se zobrazí a poskytuje identifikátor URI spuštěné služby a identifikátor URI HTML stránka pro spuštěnou službu nápovědy.  
  
3.  Ukázka běží, klient odešle požadavky do služby a zapíše odpovědi do okna konzoly. Všimněte si různých formátech odpovědí: XML, JSON, Atom a XHTML.  
  
4.  Zobrazí se výzva k procházení k identifikátoru URI, ve kterém můžete požádat o odpovědi ve formátu .jpeg. Otevřete prohlížeč a přejděte na daný identifikátor URI.  
  
5.  Stisknutím libovolné klávesy ukončit vzorku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a>Viz také
