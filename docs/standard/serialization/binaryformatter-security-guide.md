---
title: Průvodce zabezpečením BinaryFormatter
description: Tento článek popisuje bezpečnostní rizika vyplývající z typu BinaryFormatter a doporučení pro použití různých serializátorů.
ms.date: 07/11/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: ac01fe78c9577563641a8b06a232ed614ed8520a
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558839"
---
# <a name="binaryformatter-security-guide"></a>Průvodce zabezpečením BinaryFormatter

Tento článek se týká následujících implementací rozhraní .NET:

* .NET Framework všechny verze
* .NET Core 2,1 – 3,1
* .NET 5,0 a novější

## <a name="background"></a>Pozadí

> [!WARNING]
> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Typ je nebezpečný a nedoporučuje ***not*** se pro zpracování dat. Aplikace by se měly přestat používat `BinaryFormatter` co nejdříve, a to i v případě, že se domnívají, že data, která zpracovávají, budou důvěryhodná. `BinaryFormatter` je nezabezpečené, nelze nastavit jako zabezpečené.

Tento článek platí také pro následující typy:

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Web.UI.ObjectStateFormatter>

Chyby zabezpečení deserializace jsou kategorie hrozby, kde jsou datové části žádosti zpracovávány nezabezpečeně. Útočník, který tato ohrožení zabezpečení úspěšně zneužije proti aplikaci, může způsobit odepření služby (DoS), zpřístupnění informací nebo vzdálené spuštění kódu uvnitř cílové aplikace. Tato kategorie rizika konzistentně zajišťuje [OWASP 10](https://owasp.org/www-project-top-ten/). Cíle zahrnují aplikace napsané v [různých jazycích](https://owasp.org/www-community/vulnerabilities/Deserialization_of_untrusted_data), včetně C/C++, Java a C#.

V rozhraní .NET je největším cílem rizika aplikace, které používají <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> typ k deserializaci dat. `BinaryFormatter` se v celém ekosystému .NET široce používá z důvodu jeho výkonu a jeho snadného použití. Stejný výkon ale poskytuje útočníkům možnost ovlivnit tok řízení v rámci cílové aplikace. Úspěšné útoky můžou vést k tomu, že útočník může spustit kód v kontextu cílového procesu.

Jako jednodušší analogie předpokládáme, že volání `BinaryFormatter.Deserialize` přes datovou část je ekvivalent interpretace této datové části jako samostatného spustitelného souboru a jeho spuštění.

## <a name="binaryformatter-security-vulnerabilities"></a>Ohrožení zabezpečení BinaryFormatter

> [!WARNING]
> `BinaryFormatter.Deserialize`Metoda není __nikdy__ bezpečná při použití s nedůvěryhodným vstupem. Důrazně doporučujeme, aby spotřebitelé místo toho měli možnost použít některou z alternativ uvedených dále v tomto článku.

`BinaryFormatter` byl implementován před tím, že chyby zabezpečení deserializace byly dobře srozumitelnější kategorie hrozeb. V důsledku toho kód nedodržuje moderní osvědčené postupy. `Deserialize`Metodu lze použít jako vektor pro útočníky k provádění útoků DOS na využívání aplikací. Tyto útoky mohou způsobit, že aplikace nereaguje nebo má za následek neočekávané ukončení procesu. U této kategorie útoku se nedá zmírnit `SerializationBinder` ani žádný jiný `BinaryFormatter` konfigurační přepínač. Rozhraní .NET považuje toto chování za ***záměrné*** a nevydá aktualizaci kódu pro úpravu chování.

`BinaryFormatter.Deserialize` může být zranitelná vůči jiným kategoriím útoku, jako je například zpřístupnění informací nebo vzdálené spuštění kódu. Používání funkcí, jako je vlastní, <xref:System.Runtime.Serialization.SerializationBinder> může být nedostatečné pro správné zmírnění těchto rizik. Existuje možnost, že bude zjištěna nová chyba zabezpečení, pro kterou rozhraní .NET nemůže prakticky publikovat aktualizaci zabezpečení. Spotřebitelé by měli vyhodnotit své jednotlivé scénáře a vzít v úvahu potenciální ozáření těchto rizik.

Zákazníkům doporučujeme, aby `BinaryFormatter` na svých aplikacích prováděli jednotlivá posouzení rizik. Je výlučným zodpovědností spotřebitele, aby bylo možné určit, jestli se má využít `BinaryFormatter` . Spotřebitelé by měli vyhodnotit zabezpečení, technickou, pověst, právní a zákonné požadavky na používání `BinaryFormatter` .

## <a name="preferred-alternatives"></a>Preferované alternativy

.NET nabízí několik integrovaných serializátorů v krabicích, které můžou bezpečně zpracovávat nedůvěryhodná data:

* <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Runtime.Serialization.DataContractSerializer> k serializaci grafů objektů do a z XML. Nepleťte si `DataContractSerializer` s  <xref:System.Runtime.Serialization.NetDataContractSerializer> .
* <xref:System.IO.BinaryReader> a <xref:System.IO.BinaryWriter> pro XML a JSON.
* <xref:System.Text.Json>Rozhraní API k serializaci grafů objektů do formátu JSON.

## <a name="dangerous-alternatives"></a>Nebezpečné alternativy

Vyhněte se následujícím serializátorům:

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.ObjectStateFormatter>

Předchozí serializátory využívají neomezenou polymorfní deserializaci a jsou nebezpečné, podobně jako `BinaryFormatter` .

## <a name="the-risks-of-assuming-data-to-be-trustworthy"></a>Rizika vyplývající z předpokladu, že data budou důvěryhodná

Vývojář aplikací se často může domnívat, že zpracovává jenom důvěryhodný vstup. Bezpečné vstupní případy jsou ve výjimečných případech pravdivé. Je ale mnohem častější, že datová část překračuje hranice vztahu důvěryhodnosti bez toho, aby ji vývojář uvědomil.

__Vezměte v úvahu Server Prem__ , kde zaměstnanci k interakci se službou používají desktopového klienta ze svých pracovních stanic. Tento scénář se může zobrazit naïvely jako "bezpečné" nastavení, kde se dá využít `BinaryFormatter` přijatelné. Tento scénář však prezentuje vektor pro malware, který získá přístup k počítači jednoho zaměstnance, aby mohl být rozložen v celém podniku. Tento malware může využít podnikového použití `BinaryFormatter` k pozdějšímu přesunu z pracovní stanice zaměstnance na back-end Server. Pak může exfiltrovat citlivá data společnosti. Taková data můžou zahrnovat obchodní tajemství nebo zákaznická data.

__Zvažte také aplikaci, která používá `BinaryFormatter` k trvalému uložení stavu.__ Může se stát, že první se jeví jako bezpečný scénář, protože čtení a zápis dat na vlastním pevném disku představuje menší hrozbu. Sdílení dokumentů v rámci e-mailu nebo Internetu je ale běžné a většina koncových uživatelů by nemusela tyto stažené soubory otevřít jako rizikové chování.

Tento scénář je možné využít k nekalé účinku. Pokud je aplikace hra, uživatelé, kteří sdílejí soubory pro ukládání souborů, jsou nevědomé. Také je možné cílit na samotné vývojáře. Útočník může poslat e-mailem technickou podporu pro vývojáře, připojit škodlivý datový soubor a požádat pracovníky podpory, aby ho otevřel. Tento druh útoku může útočníkovi umožnit dostane v podniku.

Dalším scénářem je, že datový soubor je uložený v cloudovém úložišti a automaticky se synchronizuje mezi počítači uživatele. Útočník, který je schopný získat přístup k účtu cloudového úložiště, může poškodit datový soubor. Tento datový soubor bude automaticky synchronizován do počítačů uživatele. Když uživatel příště otevře datový soubor, spustí se datová část útočníka. Útočník tak může zneužít ohrožení zabezpečení účtu cloudového úložiště, aby získal úplná oprávnění ke spouštění kódu.

__Vezměte v úvahu aplikaci, která se pohybuje od stolního modelu instalace do modelu cloudového modelu.__ Tento scénář zahrnuje aplikace, které se pohybují z desktopové aplikace nebo z modelu klienta s bohatou platností do webového modelu. Jakékoli modely hrozeb vycházející z desktopové aplikace nemusí nutně platit pro cloudovou službu. Model hrozeb pro aplikaci klasické pracovní plochy může tuto hrozbu zavřít jako nezajímavou, aby klient mohl sami napadnout. Tato hrozba ale může být zajímavá, když považuje vzdáleného uživatele (klienta) o útok na samotnou cloudovou službu.

> [!NOTE]
> Obecně platí, že záměrem serializace je přenést objekt do nebo z aplikace. Při uplatnění modelování hrozeb se téměř vždy označuje tento druh přenosu dat jako přeložení hranice vztahu důvěryhodnosti.

## <a name="further-resources"></a>Další zdroje informací

* [YSoSerial.NET](https://github.com/pwntester/ysoserial.net) se na to, jakým způsobem aplikace nežádoucí osoby útoku využívají `BinaryFormatter` .
* Obecné základní informace o slabých číslech zabezpečení:
  * [OWASP Top 10-A8:2017 – nezabezpečená deserializace](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A8-Insecure_Deserialization)
  * [CWE-502: deserializace nedůvěryhodných dat](https://cwe.mitre.org/data/definitions/502.html)
