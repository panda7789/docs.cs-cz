---
title: Integrace mezipaměti ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: c541f3caad8a500b9fdb33d00b58706bac876e37
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594748"
---
# <a name="aspnet-caching-integration"></a>Integrace mezipaměti ASP.NET

Tato ukázka předvádí, jak využít výstupní mezipaměť ASP.NET s modelem programování webového HTTP WCF. Toto téma se zaměřuje na funkci integrace výstupní mezipaměti ASP.NET.

## <a name="demonstrates"></a>Demonstruje

Integrace s výstupní mezipamětí ASP.NET

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a>Účely

Ukázka používá pro použití <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ukládání výstupu ASP.NET do mezipaměti s využitím služby Windows Communication Foundation (WCF). <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>Je aplikován na operace služby a poskytuje název profilu mezipaměti v konfiguračním souboru, který by měl být použit na odpovědi z dané operace.

V souboru Service.cs ukázkového projektu služby `GetCustomer` `GetCustomers` jsou operace a označeny pomocí <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> příkazu, který poskytuje název profilu mezipaměti "CacheFor60Seconds". V souboru Web. config projektu služby je profil mezipaměti "CacheFor60Seconds" uveden pod < `caching` > prvek < `system.web` >. Pro tento profil mezipaměti `duration` je hodnota atributu "60", takže odpovědi spojené s tímto profilem jsou uloženy v mezipaměti ve výstupní mezipaměti ASP.NET po dobu 60 sekund. Také pro tento profil mezipaměti `varmByParam` je atribut nastaven na "formát", takže požadavky s různými hodnotami pro `format` parametr řetězce dotazu mají své odpovědi v mezipaměti odděleně. Nakonec atribut profilu mezipaměti `varyByHeader` je nastaven na hodnotu přijmout, takže požadavky s různými hodnotami Accept Header mají své odpovědi v mezipaměti odděleně.

Program.cs v klientském projektu ukazuje, jak může být takový klient vytvořen pomocí <xref:System.Net.HttpWebRequest> . Všimněte si, že toto je pouze jeden způsob, jak získat přístup ke službě WCF. Ke službě je také možné přistupovat pomocí jiných tříd .NET Framework, jako je například objekt pro vytváření kanálů WCF a <xref:System.Net.WebClient> . Další ukázky v sadě SDK (například základní ukázka [služby http](basic-http-service.md) ) ilustrují způsob použití těchto tříd ke komunikaci se službou WCF.

## <a name="to-run-the-sample"></a>Chcete-li spustit ukázku

Ukázka se skládá ze tří projektů:

- **Služba**: projekt webové aplikace, který obsahuje službu WCF http hostovanou v ASP.NET.

- **Klient**: projekt konzolové aplikace, který provádí volání služby.

- **Společné**: sdílená knihovna, která obsahuje typ zákazníka používaný klientem a službou.

Při spuštění aplikace konzoly klienta provede klient požadavek na službu a zapíše příslušné informace z odpovědí do okna konzoly.

#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku

1. Otevřete řešení pro ukázkovou integraci ASP.NET pro ukládání do mezipaměti.

2. Stisknutím kláves CTRL+SHIFT+B řešení sestavíte.

3. Pokud okno **Průzkumník řešení** ještě není otevřené, stiskněte Ctrl + W + S.

4. V okně **Průzkumník řešení** klikněte pravým tlačítkem na projekt **služby** a vyberte **spustit novou instanci**. Tím se spustí vývojový server ASP.NET, který je hostitelem služby.

5. V okně **Průzkumník řešení** klikněte pravým tlačítkem na projekt **klienta** a vyberte **spustit novou instanci**.

6. Zobrazí se okno Konzola klienta, ve kterém je uveden identifikátor URI běžící služby a identifikátor URI stránky s nápovědu HTML pro běžící službu. V jakémkoli okamžiku můžete zobrazit stránku HTML Help zadáním identifikátoru URI stránky s nastavením v prohlížeči.

7. Po spuštění ukázkového klienta zapíše klient stav aktuální aktivity.

8. Stisknutím libovolné klávesy ukončete konzolovou aplikaci klienta.

9. Stisknutím SHIFT + F5 zastavíte ladění služby.

10. V oznamovací oblasti systému Windows klikněte pravým tlačítkem myši na ikonu vývojového serveru ASP.NET a vyberte **zastavit**.
