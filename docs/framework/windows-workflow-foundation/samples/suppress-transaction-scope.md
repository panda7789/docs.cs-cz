---
title: Potlačení oboru transakcí
ms.date: 03/30/2017
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
ms.openlocfilehash: 44814d66a4de4b3e72bb33eb46019eb1088ab040
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385191"
---
# <a name="suppress-transaction-scope"></a>Potlačení oboru transakcí
Vzorek ukazuje, jak vytvořit vlastní `SuppressTransactionScope` aktivity k potlačení okolí transakce za běhu, pokud jsou k dispozici.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Vlastní aktivita je užitečné zabránit transakce se tok si do jiné služby pokud tok transakcí nežádoucí u určitého scénáře. Modul runtime pracovního postupu obsahuje integrovanou podporu pro potlačení v okolí transakce <xref:System.Activities.NativeActivity> třídy, ale chcete-li použít tuto podporu, je potřeba vytvořit vlastní <xref:System.Activities.NativeActivity> jako je třeba v této ukázce.  
  
 Tento scénář se skládá ze tří částí. První, <xref:System.Activities.Statements.TransactionScope> vytvoří, který se stane okolí transakce za běhu. To je ověřováno vlastní aktivitu, která vytiskne identifikátory místní a distribuované transakce. Transakce je poté naplněn vzdálené služby před zahájením druhé části. Během druhé části pracovního postupu přejde `SuppressTransactionScope` a znovu se opakuje proces tisku identifikátory transakce a tok transakce. Ale vlastní aktivity nenajde okolí transakce a zprávy byly převedeny do služby neobsahuje transakce. V důsledku toho služba vytvoří transakce, která znamená, že ID distribuované vytisknout na klienta a služby se neshodují. Poslední část dojde poté, co `SuppressTransactionScope` ukončí a znovu transakce za běhu bude okolí, jak ověřit pomocí jiného zpráv ve službě distribuované identifikátorem, který odpovídá identifikátor první zprávy.  
  
 Aktivita samotného je odvozena z <xref:System.Activities.NativeActivity> protože musíte naplánovat podřízené aktivity a přidejte vlastnost spuštění. `SuppressTransactionScope` Má <xref:System.Activities.Variable> typu <xref:System.Activities.RuntimeTransactionHandle>, které musí být využity místo pole instance typu <xref:System.Activities.RuntimeTransactionHandle> protože popisovače musí být inicializován. `Variable<RuntimeTransactionHandle>` Se přidá do metadat aktivity jako proměnnou implementace vzhledem k tomu slouží pouze interně.  
  
 Při spuštění aktivity ji nejprve zkontroluje, zda byl zadán text a pokud ano, nastaví `SuppressTransaction` vlastnost <xref:System.Activities.RuntimeTransactionHandle>. Jakmile je vlastnost nastavena, je přidán k vlastnostem, provádění a stane okolí. To znamená, že všechny aktivity, který je podřízeným prvkem `SuppressTransactionScope` může zobrazit vlastnosti a proto vynucuje potlačení běhové transakce a způsobí, že vnořený <xref:System.Activities.Statements.TransactionScope> vyvolají výjimku. Jakmile popisovače je přidán k vlastnostem, spuštění, že text je naplánováno spuštění.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení SuppressTransactionScope.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
3.  Po úspěšném sestavení, klikněte pravým tlačítkem na řešení a vyberte **nastavit projekty po spuštění**. V dialogovém okně vyberte **více projektů po spuštění** a zajistit akci pro oba projekty **Start**.  
  
4.  Stiskněte F5 nebo vyberte **spustit ladění** z **ladění** nabídky. Alternativně můžete stisknutím kláves CTRL + F5 nebo vyberte **spustit bez ladění** z **ladění** nabídky spustit bez ladění.  
  
    > [!NOTE]
    >  Na serveru musí běžet před spuštěním klienta. Výstup z okna konzoly, který je hostitelem služby označuje, kdy byla spuštěna.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`