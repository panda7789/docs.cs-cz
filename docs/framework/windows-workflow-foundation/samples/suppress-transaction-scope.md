---
title: "Potlačit oboru transakce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e95262fc1aee6efb6fe63f06530b70c7c16f64b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="suppress-transaction-scope"></a>Potlačit oboru transakce
Ukázka ukazuje, jak vytvořit vlastní `SuppressTransactionScope` aktivity k potlačení vedlejším spuštění transakce, pokud je k dispozici.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Vlastní aktivita je užitečné, aby se zabránilo transakce z se plynoucích se k jiné službě Pokud toku transakcí není žádoucí pro konkrétní scénář. Má integrovanou podporu pro potlačení vedlejším transakce v modulu runtime pracovního postupu <xref:System.Activities.NativeActivity> třídu, ale chcete-li použít tato podpora je potřeba vytvořit vlastní <xref:System.Activities.NativeActivity> jako je třeba v této ukázce.  
  
 Tento scénář se skládá ze tří částí. První, <xref:System.Activities.Statements.TransactionScope> vytvoří spuštění transakce, který se stává vedlejším. Je to ověřit pomocí vlastní aktivity, která vytiskne identifikátory místní a distribuované transakce. Transakce je pak předávány vzdálené služby před zahájením druhé části. Během druhé části vstupuje do pracovního postupu `SuppressTransactionScope` a znovu se opakuje proces tisku identifikátory transakce a předávaných transakce. Ale vlastní aktivita nenajde vedlejším transakce a zpráva předávány služby neobsahuje transakce. V důsledku toho služba vytvoří transakce, což znamená distribuované ID vytištěné na klienta a služby se neshodují. Poslední část dojde po `SuppressTransactionScope` ukončí a opakujte spuštění transakce stane vedlejším, jak ověřit pomocí další zprávu ve službě distribuované identifikátorem, který odpovídá identifikátor první zprávy.  
  
 Samotný aktivity je odvozena z <xref:System.Activities.NativeActivity> protože musíte naplánovat podřízené aktivity a přidat provádění vlastnost. `SuppressTransactionScope` Má <xref:System.Activities.Variable> typu <xref:System.Activities.RuntimeTransactionHandle>, které se musí použít místo poli instance typu <xref:System.Activities.RuntimeTransactionHandle> protože popisovač musí být inicializován. `Variable<RuntimeTransactionHandle>` Je přidat do aktivity metadat jako na proměnnou implementace protože používá se pouze interně.  
  
 Při spuštění aktivity nejdřív zkontroluje, zda byl zadán text a pokud ano, nastaví `SuppressTransaction` vlastnost <xref:System.Activities.RuntimeTransactionHandle>. Jakmile je vlastnost nastavena, přidá se do vlastnosti zpracování a stane vedlejším. To znamená, že všechny aktivity, která je podřízená `SuppressTransactionScope` je schopen naleznete ve vlastnosti a proto vynucuje potlačení spuštění transakce a způsobí, že vnořený <xref:System.Activities.Statements.TransactionScope> vyvolá výjimku. Jakmile popisovač je přidat do vlastnosti provádění že textu je naplánováno spuštění.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení SuppressTransactionScope.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
3.  Po sestavení proběhla úspěšně, klikněte pravým tlačítkem na řešení a vyberte **nastavit projekty po spuštění**. V dialogovém okně vyberte **více projektů po spuštění** a zajistit akci pro oba projekty **spustit**.  
  
4.  Stisknutím klávesy F5 nebo vyberte **spustit ladění** z **ladění** nabídky. Alternativně můžete stisknutím kláves CTRL + F5 nebo vybrat **spustit bez ladění** z **ladění** nabídku spustit bez ladění.  
  
    > [!NOTE]
    >  Server musí být spuštěn před spuštěním klienta. Výstup z okna konzoly, který je hostitelem služby určuje, kdy bylo zahájeno.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="see-also"></a>Viz také
