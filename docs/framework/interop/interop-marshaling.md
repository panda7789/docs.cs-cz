---
title: Zařazování spolupráce
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, COM interop
- interop marshaling
- interop marshaling, about interop marshaling
ms.assetid: 115f7a2f-d422-4605-ab36-13a8dd28142a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7dbba5161c1eeecef41e93c908752410acbd956
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221248"
---
# <a name="interop-marshaling"></a>Zařazování spolupráce
<a name="top"></a> Zařazování spolupráce řídí, jak se data předaná v metoda argumentů a vrácené hodnoty mezi spravovaným a nespravovaným paměti během volání. Zařazování spolupráce je za běhu aktivity prováděné common language runtime zařazovací služby.  
  
 Většina datových typů mají společné reprezentací v paměti spravovaných i nespravovaných. Tyto typy interoperační zařazovač zpracuje za vás. Jiné typy mohou být nejednoznačná nebo není zastoupené vůbec ve spravované paměti.  
  
 Nejednoznačný typ, který může mít více nespravované reprezentace, které mapují na jeden spravovaný typ nebo chybějící informace o typu, jako je například velikost pole. Pro dvojznačné typy aby zařazování odvozovalo poskytuje reprezentaci výchozí a alternativní zobrazení, kde existuje více reprezentací. Můžete zadat explicitní pokynů zařazovacího modulu na to, jak je nejednoznačný typ přeuspořádat.  
  
 Tento přehled obsahuje následující části:  
  
-   [Vyvolání platformy a modely spolupráce COM](#platform_invoke_and_com_interop_models)  
  
-   [Zařazování a objekty apartment modelu COM](#marshaling_and_com_apartments)  
  
-   [Zařazování Vzdálená volání](#marshaling_remote_calls)  
  
-   [Související témata](#related_topics)  
  
-   [Referenční informace](#reference)  
  
<a name="platform_invoke_and_com_interop_models"></a>   
## <a name="platform-invoke-and-com-interop-models"></a>Vyvolání platformy a modely spolupráce COM  
 Modul common language runtime poskytuje dva mechanismy pro spolupráce s nespravovaným kódem:  
  
-   Nespravovaného kódu, což umožňuje spravovanému kódu volat exportované funkce z nespravované knihovny.  
  
-   Komunikace s objekty COM, která umožňuje spravovanému kódu pracovat s objekty modelu COM (Component Object) prostřednictvím rozhraní.  
  
 Vyvolání obě platformy a modelu COM interop použití zařazování spolupráce přesně argumenty metody přesouvat mezi volajícím a volaný a zpět, pokud vyžaduje. Jak ukazuje následující obrázek, platformu vyvolání toky volání metody ze spravovaného do nespravovaného kódu a nikdy jiným způsobem, kromě případů, kdy [funkce zpětného volání](callback-functions.md) se využívá řada. I v případě vyvolání platformy můžete tok volání pouze ze spravovaného do nespravovaného kódu, může tok dat v obou směrech jako vstupní nebo výstupní parametry. Volání metody vzájemné spolupráce COM můžete tok v obou směrech.  
  
 ![Vyvolání platformy](./media/interopmarshaling.png "interopmarshaling")  
Vyvolání platformy a tok volání interop modelu COM  
  
 Na nejnižší úrovni obou mechanismy používají stejný zprostředkovatel komunikace s objekty zařazování služby; ale některé typy dat podporovaných výhradně ve spolupráci s COM nebo vyvolání platformy. Podrobnosti najdete v tématu [výchozí chování zařazování](default-marshaling-behavior.md).  
  
 [Zpět na začátek](#top)  
  
<a name="marshaling_and_com_apartments"></a>   
## <a name="marshaling-and-com-apartments"></a>Zařazování a objekty apartment modelu COM  
 Interoperační zařazovač zařadí data mezi běžné haldě modulu runtime jazyka a nespravované haldě. Zařazování vyvolá se při každém volajícím a volaným nelze použít ve stejné instanci data. Interoperační zařazovač umožňuje volajícím a volaným provoz na stejná data, i v případě, že mají své vlastní kopie dat se zobrazí.  
  
 COM také obsahuje zařazovací modul, který zařadí data mezi objekty apartment modelu COM nebo jiné procesy COM. Při volání mezi spravovaný a nespravovaný kód v rámci stejného objektu apartment modelu COM, interoperační zařazovač je potřebný jenom zařazování. Při volání mezi spravovaný kód a nespravovaný kód v různých apartment modelu COM nebo jiným procesem, interoperační zařazovač a zařazovacího modulu COM souvisejí.  
  
### <a name="com-clients-and-managed-servers"></a>Klienti modelu COM a spravovaných serverů  
 Registrovaných exportované spravovaný server pomocí knihovny typů [Regasm.exe (Nástroj registrace sestavení)](../tools/regasm-exe-assembly-registration-tool.md) má `ThreadingModel` záznam v registru nastavte na `Both`. Tato hodnota označuje, že server možné ho aktivovat v jednovláknový apartment (STA) nebo s více vlákny typu apartment (MTA). Objekt serveru se vytvoří ve stejném objektu apartment jako volající funkci, jak je znázorněno v následující tabulce.  
  
|Klient modelu COM|.NET serveru|Požadavky zařazování|  
|----------------|-----------------|-----------------------------|  
|STA|`Both` změní STA.|Zařazování stejného objektu apartment.|  
|MTA|`Both` změní MTA.|Zařazování stejného objektu apartment.|  
  
 Protože klient a server jsou ve stejném objektu apartment, zprostředkovatel komunikace s objekty zařazování service automaticky zpracovává všechna data zařazování. Následující obrázek znázorňuje spolupráce zařazovací služby provoz mezi spravovanými a nespravovanými haldy v rámci stejného objektu apartment modelu COM-style.  
  
 ![Zařazování spolupráce](./media/interopheap.gif "interopheap")  
Proces zařazování stejného objektu apartment  
  
 Pokud budete chtít exportovat spravovaného serveru, mějte na paměti, určuje klient modelu COM typu apartment serveru. Spravovaný server volá klient modelu COM ve MTA inicializovat, musíte zajistit bezpečný přístup z více vláken.  
  
### <a name="managed-clients-and-com-servers"></a>Spravovaných klientů a serverů modelu COM  
 Výchozí nastavení pro objekty apartment spravovaného klienta je MTA; aplikace typu klient .NET však můžete změnit výchozí nastavení. Například [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] objektu apartment nastavení klienta je STA. Můžete použít <xref:System.STAThreadAttribute?displayProperty=nameWithType>, <xref:System.MTAThreadAttribute?displayProperty=nameWithType>, <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> vlastnost, nebo <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType> vlastnost sloužící ke zkoumání a změnit nastavení objektu apartment spravovaný klient.  
  
 Autor součásti nastaví spřažení vláken COM serveru. V následující tabulce jsou uvedeny kombinace nastavení objektu apartment pro klienty .NET a serverů modelu COM. Profil také ukazuje, výsledná zařazování požadavky pro všechny kombinace.  
  
|Klient .NET|COM server|Požadavky zařazování|  
|-----------------|----------------|-----------------------------|  
|MTA (výchozí)|MTA<br /><br /> STA|Zařazování spolupráce.<br /><br /> Zprostředkovatel komunikace s objekty a modelu COM zařazování.|  
|STA|MTA<br /><br /> STA|Zprostředkovatel komunikace s objekty a modelu COM zařazování.<br /><br /> Zařazování spolupráce.|  
  
 Když klienta spravovaného a nespravovaného serveru jsou ve stejném objektu apartment, zprostředkovatele komunikace s objekty zařazování služby zpracovává všechny zařazování dat. Ale když klienta a serveru jsou inicializovány v jiné objekty apartment, zařazování COM je také nutný. Následující obrázek znázorňuje prvky volání mezi objektu apartment.  
  
 ![Zařazování COM](./media/singleprocessmultapt.gif "singleprocessmultapt")  
Volání mezi apartment mezi klient .NET a objekt modelu COM  
  
 Pro různé apartment zařazování, máte následující:  
  
-   Přijměte režie zařazování mezi apartment, což je patrné pouze v případě, že existují mnoho volání přes hranice. Je nutné zaregistrovat knihovnu typů komponenty modelu COM pro volání úspěšně překračují hranice objektu apartment.  
  
-   Příkaz ALTER hlavního vlákna nastavením klienta vlákna STA nebo MTA. Například pokud vaše C# klient volá řada komponent STA COM, můžete vyhnout tak, že nastavíte hlavního vlákna STA. zařazování mezi objektu apartment  
  
    > [!NOTE]
    >  Jednou vlákno C# klienta nastavena na STA, volání součásti MTA COM bude vyžadovat zařazování mezi objektu apartment.  
  
 Explicitně zvolíte modelu objektu apartment, v tématu [spravovaná a nespravovaná vlákna](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100)).  
  
 [Zpět na začátek](#top)  
  
<a name="marshaling_remote_calls"></a>   
## <a name="marshaling-remote-calls"></a>Zařazování Vzdálená volání  
 Stejně jako u zařazování mezi apartment modelu COM zařazování je zahrnuta v každé volání mezi spravovaný a nespravovaný kód pokaždé, když se objekty nacházejí v samostatných procesech. Příklad:  
  
-   Klient modelu COM, která volá spravovaný server na vzdáleného hostitele používá distributed COM (DCOM).  
  
-   Spravovaný klient, který volá server COM na vzdáleného hostitele používá model DCOM.  
  
 Následující obrázek znázorňuje, jak spolupráce zařazování a zařazování COM poskytují komunikační kanály přes hranice procesu a hostitele.  
  
 ![Zařazování COM](./media/interophost.gif "interophost")  
Zařazování mezi procesy  
  
### <a name="preserving-identity"></a>Zachování Identity  
 Modul common language runtime uchovává identity spravovaných a nespravovaných odkazy. Následující obrázek znázorňuje tok nespravované přímé odkazy (horní řádek) a s přímým přístupem spravované odkazy (dolní řádek) přes hranice procesu a hostitele.  
  
 ![Obálka volatelná aplikacemi COM a obálka volatelná za běhu](./media/interopdirectref.gif "interopdirectref")  
Odkaz na předávání přes hranice procesu a hostitele  
  
 Na tomto obrázku:  
  
-   Nespravovaný klient získá odkaz na objekt modelu COM ze spravovaného objektu, který získá tento odkaz na vzdáleného hostitele. Je mechanismus vzdálenou komunikaci modelu DCOM.  
  
-   Spravovaný klient získá odkaz na spravovaný objekt z objektu COM, který získá tento odkaz na vzdáleného hostitele. Je mechanismus vzdálenou komunikaci modelu DCOM.  
  
    > [!NOTE]
    >  Exportované knihovny typů spravovaného serveru musí být zaregistrovaný.  
  
 Počet hranice procesů mezi volajícím a volaným je bezvýznamná; stejné přímé odkazování vyvolá pro volání a mimo proces.  
  
### <a name="managed-remoting"></a>Spravované vzdálené komunikace  
 Modul runtime poskytuje také spravované vzdálené komunikace, které můžete použít k vytvoření komunikačního kanálu mezi spravovanými objekty přes hranice procesu a hostitele. Spravované vzdálené komunikace zvládne brány firewall mezi komunikujícími komponenty, jako ukazuje následující obrázek.  
  
 ![Protokol SOAP nebo TcpChannel](./media/interopremotesoap.gif "interopremotesoap")  
Vzdálená volání přes brány firewall pomocí protokolu SOAP nebo TcpChannel třídy  
  
 Některá volání nespravovaného můžete channeled prostřednictvím protokolu SOAP, jako je například volání mezi obsluhované komponenty a modelu COM.  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Výchozí chování zařazování](default-marshaling-behavior.md)|Popisuje pravidla, která používá službu zařazování interop zařazování dat.|  
|[Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)|Popisuje, jak deklarovat parametry metody a předání argumentů funkcí exportovaných knihovnou nespravovaných knihoven.|  
|[Zařazování dat se spoluprací COM](marshaling-data-with-com-interop.md)|Popisuje, jak přizpůsobit COM – obálky změnit chování zařazování.|  
|[Postupy: Migrace spravovaného kódu DCOM do WCF](how-to-migrate-managed-code-dcom-to-wcf.md)|Popisuje postup migrace z modelu DCOM do WCF.|  
|[Postupy: Mapování výsledků HRESULT a výjimek](how-to-map-hresults-and-exceptions.md)|Popisuje, jak namapovat vlastní výjimky výsledků HRESULT a poskytuje úplné mapování z každé HRESULT na jeho třída srovnatelné výjimek v rozhraní .NET Framework.|  
|[Spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))|Popisuje akce, které jsou podporovány při použití obecných typů pro interoperabilitu COM.|  
|[Spolupráce s nespravovaným kódem](index.md)|Popisuje interoperability poskytované modulem common language runtime.|  
|[Rozšířená interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))|Obsahuje odkazy na další informace o začlenění komponenty modelu COM do vaší aplikace rozhraní .NET Framework.|  
|[Aspekty návrhu pro spolupráci](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))|Poskytuje tipy pro psaní integrované komponenty modelu COM.|  
  
 [Zpět na začátek](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.Runtime.InteropServices?displayProperty=nameWithType>  
  
 [Zpět na začátek](#top)
