---
title: "Pouze služba základní XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 004a37682b855135998ef4620e673421f769326d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="basic-xaml-only-service"></a>Pouze služba základní XAML
Tento příklad znázorňuje způsob vytvoření služby pouze XAML. Tento scénář je služba diagnostiky pro problémy související s Auto. Služba se implementuje jako pracovní postup, který klient zeptá na několik otázek a diagnostikovat problém. Existují dva typy službu lze diagnostikovat problémy (car nezačíná ani klimatizace nepracuje). Pracovní postup používá šablonu požadavek nebo odpověď z Návrháře ke zveřejnění tři operací jednoduché služby. Služba je hostovaná ve službě IIS tak, že vytvoříte virtuální adresář ve službě IIS a kopírování service1.xamlx a souborů Web.config do virtuálního adresáře, žádné zkompilovaný kód je požadovaná. Ve výchozím nastavení tato ukázka automaticky zkopíruje potřebné soubory do virtuální adresář vytvořen, pokud budete postupovat podle pokynů instalačního programu pro ukázky WCF a WF: [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) při sestavení v sadě Visual Studio 2010.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Načtení projektu řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.  
  
2.  Spusťte klientskou aplikaci vygenerovaných \Client\bin\debug [základní adresář řešení].  
  
3.  Aplikace vytiskne možnosti, vybere možnost. Aplikace se pak požádá otázky, odpovědi je Ano nebo ne (pomocí klíče A/N). Pokud se provádí služba diagnostice problémů, vytiskne aplikace diagnostiku.  
  
4.  Aplikace přejde zpět na možnosti. Můžete diagnostikovat jiný problém nebo ukončit aplikaci.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`