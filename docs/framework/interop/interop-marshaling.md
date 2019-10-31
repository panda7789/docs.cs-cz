---
title: Zařazování spolupráce
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, COM interop
- interop marshaling
- interop marshaling, about interop marshaling
ms.assetid: 115f7a2f-d422-4605-ab36-13a8dd28142a
ms.openlocfilehash: 70514811a9d236dc485f64fc34297cdb057a1512
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124278"
---
# <a name="interop-marshaling"></a>Zařazování spolupráce

Zařazování spolupráce určuje, jak jsou data předávána v argumentech metody a návratové hodnoty mezi spravovanou a nespravovanou pamětí během volání. Zařazování Interop je běhová aktivita prováděná zařazováním služby Common Language Runtime.

Většina datových typů má běžné reprezentace v spravované i nespravované paměti. Zařazovací modul Interop tyto typy zpracovává za vás. Jiné typy mohou být dvojznačné nebo nejsou ve spravované paměti zastoupeny vůbec.

Nejednoznačný typ může mít buď více nespravovaných reprezentací, které jsou mapovány na jeden spravovaný typ, nebo chybějící informace o typu, například velikost pole. Pro dvojznačné typy zařazovací modul poskytuje výchozí reprezentaci a alternativní reprezentace, u nichž existuje více reprezentujes. Zařazovacímu objektu můžete zadat explicitní pokyny k zařazení nejednoznačného typu.

## <a name="platform-invoke-and-com-interop-models"></a>Volání platforem a modely spolupráce modelu COM

Modul CLR (Common Language Runtime) poskytuje dva mechanismy pro spolupráci s nespravovaným kódem:

- Vyvolání platformy, které umožňuje spravovanému kódu volat funkce exportované z nespravované knihovny.
- Zprostředkovatel komunikace s objekty COM, který umožňuje spravovanému kódu pracovat s objekty modelu COM (Component Object Model) prostřednictvím rozhraní.

Volání metody a zprostředkovatel komunikace s objekty COM používají interop marshaling k přesnému přesunu argumentů mezi volajícím a volaným a zpětným voláním v případě potřeby. Jak ukazuje následující obrázek, metoda vyvolání platformy volá toky ze spravovaného do nespravovaného kódu a nikdy jiný způsob, s výjimkou případů, kdy jsou zapojeny [funkce zpětného volání](callback-functions.md) . I když volání vyvolání platformy mohou směrovat pouze ze spravovaného do nespravovaného kódu, data mohou být v obou směrech předávána jako vstupní nebo výstupní parametry. Volání metod Interop modelu COM mohou tok v obou směrech.

![Vyvolání platformy](./media/interop-marshaling/interop-marshaling-invoke-and-com.png "Volání platformy a tok volání Interop modelu COM")

Na nejnižší úrovni oba mechanismy používají stejnou službu interop marshaling; Některé typy dat jsou však podporovány výhradně pomocí zprostředkovatele komunikace s objekty COM nebo voláním platformy. Podrobnosti najdete v tématu [výchozí chování zařazování](default-marshaling-behavior.md).

## <a name="marshaling-and-com-apartments"></a>Zařazování a COM Apartment

Zařazovací modul Interop zařazuje data mezi haldou společného jazykového modulu runtime a nespravovanou haldou. Zařazování probíhá vždy, když volající a volaný nemůže pracovat na stejné instanci dat. Zařazovací modul interoperability umožňuje volajícímu a volanému, aby mohl být provozován na stejných datech, i když mají svou vlastní kopii dat.

Model COM má také zařazovací modul, který zařazování dat mezi objekty COM Apartment nebo různými procesy COM. Při volání mezi spravovaným a nespravovaným kódem v rámci stejného objektu COM Apartment je zařazovací modul interoperability jediným zařazovacím objektem. Při volání mezi spravovaným kódem a nespravovaným kódem v jiném izolovaném modelu COM nebo jiném procesu jsou zapojeny i zařazovací a zařazovací modul COM.

### <a name="com-clients-and-managed-servers"></a>Klienti modelu COM a spravované servery

Exportovaný spravovaný server s knihovnou typů zaregistrovanou modulem [Regasm. exe (nástroj registrace sestavení)](../tools/regasm-exe-assembly-registration-tool.md) má položku `ThreadingModel` registru nastavenou na `Both`. Tato hodnota indikuje, že server může být aktivovaný v prostředí STA (Single-threaded Apartment) nebo v modelu MTA (Apartment). Objekt serveru je vytvořen ve stejném typu Apartment jako jeho volající, jak je znázorněno v následující tabulce:

|Klient modelu COM|Server .NET|Požadavky zařazování|
|----------------|-----------------|-----------------------------|
|REŽIMU|`Both` se přestanou STA.|Zařazování do stejného typu apartment.|
|Agent|`Both` se stávají jako MTA.|Zařazování do stejného typu apartment.|

Vzhledem k tomu, že klient a Server jsou ve stejném typu apartment, služba interop marshaling automaticky zpracovává všechna zařazování dat. Následující ilustrace znázorňuje interop marshaling službu, která je provozována mezi spravovanými a nespravovanými haldami v rámci stejného typu Apartment ve stylu COM.

![Spolupráce při zařazování mezi spravovanými a nespravovanými haldami](./media/interop-marshaling/interop-heaps-managed-and-unmanaged.gif "Proces zařazování stejného typu Apartment")

Pokud plánujete exportovat spravovaný server, uvědomte si, že klient COM určí byt serveru. Spravovaný server, který je volán klientem modelu COM inicializovaným v modelu MTA, musí zajistit bezpečnost vlákna.

### <a name="managed-clients-and-com-servers"></a>Spravované klienty a servery COM

Výchozím nastavením pro objekty Apartment spravovaného klienta je MTA; Typ aplikace klienta .NET však může změnit výchozí nastavení. Například Visual Basic nastavení klienta Apartment je STA. K prohlédnutí a změně nastavení bytu spravovaného klienta můžete použít <xref:System.STAThreadAttribute?displayProperty=nameWithType>, <xref:System.MTAThreadAttribute?displayProperty=nameWithType>, vlastnost <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> nebo vlastnost <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType>.

Autor komponenty nastaví spřažení vlákna pro server COM. V následující tabulce jsou uvedeny kombinace nastavení bytu pro klienty rozhraní .NET a servery COM. Zobrazuje také výsledné požadavky na zařazování pro kombinace.

|Klient .NET|Server COM|Požadavky zařazování|
|-----------------|----------------|-----------------------------|
|MTA (výchozí)|Agent<br /><br /> REŽIMU|Zařazování Interop.<br /><br /> Interoperabilita a zařazování modelu COM.|
|REŽIMU|Agent<br /><br /> REŽIMU|Interoperabilita a zařazování modelu COM.<br /><br /> Zařazování Interop.|

Pokud jsou spravovaný klient a nespravovaný Server ve stejném typu apartment, služba interop marshaling zpracovává všechna zařazování dat. Pokud je ale klient a server inicializovaný v různých podsystémech, vyžaduje se také zařazování COM. Následující ilustrace znázorňuje prvky volání křížového typu:

![Zařazování modelu COM](./media/interop-marshaling/single-process-across-multi-apartment.gif "Volání mezi klienty .NET a objektem COM")

Pro zařazování mezi platformami můžete provádět následující akce:

- Přijměte režii k zařazování mezi jednotlivými platformami, což je patrné jenom v případě, že hranice obsahuje mnoho volání. Je nutné zaregistrovat knihovnu typů komponenty modelu COM pro volání úspěšného křížení hranice objektu apartment.
- Změňte hlavní vlákno nastavením vlákna klienta na STA nebo MTA. Například pokud váš C# klient volá mnoho komponent modelu COM STA, můžete se vyhnout zařazování na více platforem nastavením hlavního vlákna na sta.

    > [!NOTE]
    > Jakmile je vlákno C# klienta nastavené na sta, budou volání komponent modelu COM MTA vyžadovat zařazování mezi prostředími.

Pokyny, jak explicitně vybrat model Apartment, najdete v tématu [spravovaná a nespravované vlákno](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100)).

## <a name="marshaling-remote-calls"></a>Zařazování vzdálených volání

Podobně jako při zařazování do více platforem je zařazování do modelu COM zapojeno do každého volání mezi spravovaným a nespravovaným kódem, kdykoli se objekty nacházejí v samostatných procesech. Příklad:

- Klient COM, který vyvolá spravovaný server na vzdáleném hostiteli, používá Distributed COM (DCOM).
- Spravovaný klient, který vyvolá server COM na vzdáleném hostiteli, používá model DCOM.

Následující obrázek ukazuje, jak interop marshaling a COM zařazování poskytují komunikační kanály napříč procesy a hranicemi hostitele:

![Zařazování modelu COM](./media/interop-marshaling/interop-and-com-marshaling.gif "Zařazování mezi procesy")

### <a name="preserving-identity"></a>Zachování identity

Modul CLR (Common Language Runtime) zachovává identitu spravovaných a nespravovaných odkazů. Následující ilustrace znázorňuje tok přímých nespravovaných odkazů (horní řádek) a přímé spravované odkazy (dolní řádek) napříč hranicemi procesu a hostitele.

![Obálka s příchodem modelu COM a vyvolané za běhu](./media/interop-marshaling/interop-direct-ref-across-process.gif "Reference procházející přes hranice procesu a hostitele")

Na tomto obrázku:

- Nespravovaný klient získá odkaz na objekt modelu COM ze spravovaného objektu, který získá tento odkaz ze vzdáleného hostitele. Mechanismus vzdálené komunikace je DCOM.
- Spravovaný klient získá odkaz na spravovaný objekt z objektu COM, který získá tento odkaz ze vzdáleného hostitele. Mechanismus vzdálené komunikace je DCOM.

    > [!NOTE]
    > Exportovaná knihovna typů spravovaného serveru musí být zaregistrovaná.

Počet hranic procesu mezi volajícím a volaným je nepodstatný; stejný přímý odkazování nastane pro volání v procesu a mimoprocesové procesy.

### <a name="managed-remoting"></a>Spravovaná Vzdálená komunikace

Modul runtime také poskytuje spravovanou vzdálenou komunikaci, kterou můžete použít k vytvoření komunikačního kanálu mezi spravovanými objekty napříč procesy a hranicemi hostitelů. Spravovaná Vzdálená komunikace může vyhovovat bráně firewall mezi komunikujícími součástmi, jak je znázorněno na následujícím obrázku:

![SOAP nebo TcpChannel](./media/interop-marshaling/interop-remote-soap-or-tcp.gif "Vzdálená volání přes brány firewall pomocí protokolu SOAP nebo třídy TcpChannel") Vzdálená volání přes brány firewall pomocí protokolu SOAP nebo třídy TcpChannel

Některé nespravované volání lze přesměrovat prostřednictvím protokolu SOAP, například volání mezi službami a komponentami COM.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Výchozí chování zařazování](default-marshaling-behavior.md)|Popisuje pravidla, která služba interop marshaling používá k zařazování dat.|
|[Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)|Popisuje, jak deklarovat parametry metody a předávat argumenty funkcím exportovaným nespravovanými knihovnami.|
|[Zařazování dat se spoluprací COM](marshaling-data-with-com-interop.md)|Popisuje, jak přizpůsobit obálky modelu COM pro změnu chování při zařazování.|
|[Postup: Migrace spravovaného kódu DCOM do WCF](how-to-migrate-managed-code-dcom-to-wcf.md)|Popisuje, jak migrovat z modelu DCOM na WCF.|
|[Postupy: Mapování výsledků HRESULT a výjimek](how-to-map-hresults-and-exceptions.md)|Popisuje, jak namapovat vlastní výjimky na HRESULTs a poskytuje úplné mapování z každého HRESULT na jeho srovnatelnou třídu výjimek v .NET Framework.|
|[Spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))|Popisuje, které akce jsou podporovány při použití obecných typů pro interoperabilitu modelu COM.|
|[Spolupráce s nespravovaným kódem](index.md)|Popisuje služby vzájemné funkční spolupráce poskytované modulem CLR (Common Language Runtime).|
|[Pokročilá interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))|Obsahuje odkazy na Další informace o zahrnutí komponent modelu COM do aplikace .NET Framework.|
|[Faktory návrhu pro spoluprovozování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))|Poskytuje tipy pro psaní integrovaných komponent modelu COM.|

## <a name="reference"></a>Odkaz

<xref:System.Runtime.InteropServices?displayProperty=nameWithType>
