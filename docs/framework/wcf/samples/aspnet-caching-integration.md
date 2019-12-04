---
title: Integrace mezipaměti ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 23c10e56dba7daec2d1027de92e8252c8fe69055
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716181"
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
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a>Účely

Ukázka používá <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> k využití ukládání výstupu do mezipaměti ASP.NET se službou Windows Communication Foundation (WCF). <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> se aplikuje na operace služby a poskytuje název profilu mezipaměti v konfiguračním souboru, který by se měl použít na odpovědi z dané operace.

V souboru Service.cs ukázkového projektu služby jsou operace `GetCustomer` i `GetCustomers` označeny <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, což poskytuje název profilu mezipaměti "CacheFor60Seconds". V souboru Web. config projektu služby je profil mezipaměti "CacheFor60Seconds" k dispozici pod <`caching`> prvek <`system.web`>. Pro tento profil mezipaměti je hodnota atributu `duration` "60", takže odpovědi spojené s tímto profilem jsou uloženy v mezipaměti ve výstupní mezipaměti ASP.NET po dobu 60 sekund. Pro tento profil mezipaměti také platí, že atribut `varmByParam` je nastaven na hodnotu "formát", takže požadavky s různými hodnotami pro parametr řetězce dotazu `format` mají své odpovědi uloženy v mezipaměti odděleně. Nakonec je atribut `varyByHeader` profilu mezipaměti nastaven na hodnotu přijmout, takže požadavky s různými hodnotami Accept Header mají své odpovědi v mezipaměti odděleně.

Program.cs v klientském projektu ukazuje, jak může být klient vytvořen pomocí <xref:System.Net.HttpWebRequest>. Všimněte si, že toto je pouze jeden způsob, jak získat přístup ke službě WCF. Ke službě je také možné přistupovat pomocí jiných tříd .NET Framework, jako je například objekt pro vytváření kanálů WCF a <xref:System.Net.WebClient>. Další ukázky v sadě SDK (například základní ukázka [služby http](../../../../docs/framework/wcf/samples/basic-http-service.md) ) ilustrují způsob použití těchto tříd ke komunikaci se službou WCF.

## <a name="to-run-the-sample"></a>Chcete-li spustit ukázku

Ukázka se skládá ze tří projektů:

- **Služba**: projekt webové aplikace, který obsahuje službu WCF http hostovanou v ASP.NET.

- **Klient**: projekt konzolové aplikace, který provádí volání služby.

- **Společné**: sdílená knihovna, která obsahuje typ zákazníka používaný klientem a službou.

Při spuštění aplikace konzoly klienta provede klient požadavek na službu a zapíše příslušné informace z odpovědí do okna konzoly.

#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku

1. Otevřete řešení pro ukázkovou integraci ASP.NET pro ukládání do mezipaměti.

2. Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.

3. Pokud okno **Průzkumník řešení** ještě není otevřené, stiskněte Ctrl + W + S.

4. V okně **Průzkumník řešení** klikněte pravým tlačítkem na projekt **služby** a vyberte **spustit novou instanci**. Tím se spustí vývojový server ASP.NET, který je hostitelem služby.

5. V okně **Průzkumník řešení** klikněte pravým tlačítkem na projekt **klienta** a vyberte **spustit novou instanci**.

6. Zobrazí se okno Konzola klienta, ve kterém je uveden identifikátor URI běžící služby a identifikátor URI stránky s nápovědu HTML pro běžící službu. V jakémkoli okamžiku můžete zobrazit stránku HTML Help zadáním identifikátoru URI stránky s nastavením v prohlížeči.

7. Po spuštění ukázkového klienta zapíše klient stav aktuální aktivity.

8. Stisknutím libovolné klávesy ukončete konzolovou aplikaci klienta.

9. Stisknutím SHIFT + F5 zastavíte ladění služby.

10. V oznamovací oblasti systému Windows klikněte pravým tlačítkem myši na ikonu vývojového serveru ASP.NET a vyberte **zastavit**.
