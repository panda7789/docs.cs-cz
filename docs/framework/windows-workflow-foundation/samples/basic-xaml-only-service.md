---
title: Pouze služba základní XAML
ms.date: 03/30/2017
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
ms.openlocfilehash: f4f296a97b9c3093874c5ec8e05023e84b0af44a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074707"
---
# <a name="basic-xaml-only-service"></a>Pouze služba základní XAML
Tento příklad ukazuje, jak vytvořit službu pouze XAML. Tento scénář je služba diagnostiky pro problémy související s automobilu. Služba se implementuje jako pracovní postup, který klient zeptá na několik otázek a Diagnostikujte problém. Existují dva typy služby můžete diagnostikovat problémy (Auto nezačíná ani klimatizace, nebudou fungovat). Pracovní postup využívá k tomu tři jednoduché servisní operace požadavku/odpovědi šablony z návrháře. Služba je hostována ve službě IIS tak, že vytvoříte virtuální adresář služby IIS a kopírování service1.xamlx a soubory Web.config do virtuálního adresáře, kompilované není vyžadován žádný kód. Ve výchozím nastavení tato ukázka automaticky zkopíruje potřebné soubory do virtuálního adresáře vytvoří, když budete postupovat podle pokynů nastavení pro ukázky WCF a WF: [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) při sestavování v sadě Visual Studio 2010.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Načítání řešení projektu v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.  
  
2.  Spuštění klientské aplikace vygenerované v \Client\bin\debug [základní adresář řešení].  
  
3.  Aplikace vytiskne možnosti, vybere možnost. Aplikace pak zobrazí několik otázek, odpovězte Ano nebo ne je (pomocí klíče A/N). Až službu diagnostikování problémů, vytiskne aplikace diagnózu.  
  
4.  Aplikace přejde zpět na možnosti. Můžete diagnostikovat jiný problém nebo ukončit aplikaci.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`