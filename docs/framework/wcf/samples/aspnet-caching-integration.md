---
title: Integrace mezipaměti ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 56f686b83deb576f1245a9d4b9df2df433ea1e2f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045781"
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
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a>Účely

Ukázka používá <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> pro použití ukládání výstupu ASP.NET do mezipaměti s využitím služby Windows Communication Foundation (WCF). <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Je aplikován na operace služby a poskytuje název profilu mezipaměti v konfiguračním souboru, který by měl být použit na odpovědi z dané operace.

V souboru Service.cs ukázkového projektu `GetCustomer` služby jsou <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>operace a `GetCustomers` označeny pomocí příkazu, který poskytuje název profilu mezipaměti "CacheFor60Seconds". V souboru Web. config projektu služby je profil mezipaměti "CacheFor60Seconds" uveden pod <`caching`> prvek <`system.web`>. Pro tento profil mezipaměti je hodnota `duration` atributu "60", takže odpovědi spojené s tímto profilem jsou uloženy v mezipaměti ve výstupní mezipaměti ASP.NET po dobu 60 sekund. Také pro tento profil `varmByParam` mezipaměti je atribut nastaven na "formát", takže požadavky s různými hodnotami `format` pro parametr řetězce dotazu mají své odpovědi v mezipaměti odděleně. Nakonec `varyByHeader` atribut profilu mezipaměti je nastaven na hodnotu přijmout, takže požadavky s různými hodnotami Accept Header mají své odpovědi v mezipaměti odděleně.

Program.cs v klientském projektu ukazuje, jak může být takový klient vytvořen pomocí <xref:System.Net.HttpWebRequest>. Všimněte si, že toto je pouze jeden způsob, jak získat přístup ke službě WCF. Ke službě je také možné přistupovat pomocí jiných tříd .NET Framework, jako je například objekt pro vytváření kanálů <xref:System.Net.WebClient>WCF a. Další ukázky v sadě SDK (například základní ukázka [služby http](../../../../docs/framework/wcf/samples/basic-http-service.md) ) ilustrují způsob použití těchto tříd ke komunikaci se službou WCF.

## <a name="to-run-the-sample"></a>Chcete-li spustit ukázku

Ukázka se skládá ze tří projektů:

- **Služba**: Projekt webové aplikace, který obsahuje službu WCF HTTP hostovanou v ASP.NET.

- **Klient**: Projekt konzolové aplikace, který provádí volání služby.

- **Běžné**: Sdílená knihovna, která obsahuje typ zákazníka, který používá klient a služba.

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
