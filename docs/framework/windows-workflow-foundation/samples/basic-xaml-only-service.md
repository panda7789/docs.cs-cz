---
title: Pouze služba základní XAML
ms.date: 03/30/2017
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
ms.openlocfilehash: aa6b6ec6930ac90fe95b1cdfcd4cb027de8e5902
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`