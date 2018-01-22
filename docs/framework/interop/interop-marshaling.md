---
title: "Zařazování spolupráce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, COM interop
- interop marshaling
- interop marshaling, about interop marshaling
ms.assetid: 115f7a2f-d422-4605-ab36-13a8dd28142a
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17638390a07f752a7101209e5635752bc0511d1d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="interop-marshaling"></a>Zařazování spolupráce
<a name="top"></a>Zařazování spolupráce řídí, jak se data předávají v metoda argumentů a návratové hodnoty mezi spravovanými a nespravovanými paměti během volání. Zařazování spolupráce je aktivita běhu zajišťuje služba zařazování modul common language runtime.  
  
 Většina datových typů mít běžných vyjádření ve spravované i nespravované paměti. Tyto typy zpracovává spolupráce vláken. Jiné typy může být nejednoznačný nebo není reprezentována vůbec v spravované paměti.  
  
 Typ nejednoznačný může mít buď více nespravované reprezentací, které jsou mapovány na jeden spravovaný typ, nebo chybějící informace o typu, jako je například velikost pole. Nejednoznačný typů poskytuje zařazování znázornění výchozí a alternativní zobrazení, kde existuje více reprezentace. Můžete zadat explicitní pokyny pro zařazování vláken v tom, jak je zařazování nejednoznačným typem.  
  
 Tento přehled obsahuje následující části:  
  
-   [Vyvolání platformy a modely zprostředkovatele komunikace s objekty COM](#platform_invoke_and_com_interop_models)  
  
-   [Marshaling a Apartment COM](#marshaling_and_com_apartments)  
  
-   [Zařazování Vzdálená volání](#marshaling_remote_calls)  
  
-   [Související témata](#related_topics)  
  
-   [Referenční informace](#reference)  
  
<a name="platform_invoke_and_com_interop_models"></a>   
## <a name="platform-invoke-and-com-interop-models"></a>Vyvolání platformy a modely zprostředkovatele komunikace s objekty COM  
 Modul common language runtime poskytuje dva mechanismy pro spolupráce s nespravovaným kódem:  
  
-   Volání nespravovaného kódu, což umožňuje spravovaného kódu k volání funkce exportované z nespravovaných knihovny.  
  
-   Spoluprací COM, umožňující spravovaného kódu k interakci s objekty modelu COM (Component Object) prostřednictvím rozhraní.  
  
 Vyvolání obě platformy a modelu COM pomocí zprostředkovatele komunikace s objekty zařazování spolupráce přesně metoda argumenty přecházet mezi volající a volaný a zpět, pokud to vyžaduje. Jak ukazuje následující obrázek, platformu vyvolání toky volání metoda ze spravovaného na nespravovaný kód a nikdy jiným způsobem, s výjimkou případů, kdy [funkce zpětného volání](../../../docs/framework/interop/callback-functions.md) se skládá. I když vyvolání platformy volání můžete toku pouze ze spravovaného na nespravovaný kód, můžete toku dat v obou směrech jako vstupní nebo výstupní parametry. Volání metody zprostředkovatele komunikace s objekty COM proudit oběma směry.  
  
 ![Vyvolání platformy](../../../docs/framework/interop/media/interopmarshaling.png "interopmarshaling")  
Vyvolání platformy a toku volání zprostředkovatele komunikace s objekty COM  
  
 Na nejnižší úrovni obou mechanismy používají stejný zprostředkovatel komunikace s objekty zařazování služby; ale některé datové typy jsou podporovány výhradně zprostředkovatel komunikace s objekty COM nebo vyvolání platformy. Podrobnosti najdete v tématu [výchozí chování zařazování](../../../docs/framework/interop/default-marshaling-behavior.md).  
  
 [Zpět na začátek](#top)  
  
<a name="marshaling_and_com_apartments"></a>   
## <a name="marshaling-and-com-apartments"></a>Marshaling a Apartment COM  
 Spolupráce vláken zařazuje dat mezi běžné haldy runtime jazyka a nespravované haldě. Zařazování dojde vždy, když volající a volaný nemůže pracovat na stejnou instanci data. Spolupráce vláken je umožněno pro volající a volaný vykazuje na stejná data i v případě, že mají své vlastní kopie dat.  
  
 COM má také vláken, která zařazuje dat mezi bytů COM nebo jiné procesy COM. Při volání mezi spravovanými a nespravovanými kódu v rámci stejné typu apartment COM, spolupráce vláken je pouze vláken zahrnutých. Při volání mezi spravovaného kódu a nespravovaného kódu v různých oddílu modelu COM nebo jiným procesem, se podílejí spolupráce vláken a COM vláken.  
  
### <a name="com-clients-and-managed-servers"></a>Klienti COM a spravovaných serverů  
 Exportovaný spravovaný server se knihovny typů registrovaných [Regasm.exe (Nástroj registrace sestavení)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) má `ThreadingModel` položky registru nastavena na `Both`. Tato hodnota označuje, že server může být aktivovaný single-threaded apartment (STA) nebo více vláken typu apartment (MTA). Objekt serveru se vytvoří ve stejné typu apartment jako jeho volajícího, jak je znázorněno v následující tabulce.  
  
|Klient COM|Rozhraní .NET serveru|Zařazování požadavky|  
|----------------|-----------------|-----------------------------|  
|STA|`Both` becomes STA.|Zařazování stejné typu apartment.|  
|MTA|`Both` becomes MTA.|Zařazování stejné typu apartment.|  
  
 Protože klient a server jsou ve stejné typu apartment, zprostředkovatel komunikace s objekty služby zařazování automaticky zpracovává všechny dat – zařazování. Následující obrázek znázorňuje službu spolupráce zařazování operační mezi spravovanými a nespravovanými haldách v rámci stejné COM stylu typu apartment.  
  
 ![Zařazování spolupráce](../../../docs/framework/interop/media/interopheap.gif "interopheap")  
Zařazování procesu stejné objektu apartment  
  
 Pokud budete chtít exportovat spravovaném serveru, mějte na paměti, že klient COM určuje typu apartment serveru. Spravovaný server volá klient modelu COM v modelu MTA inicializovat musí zajistit bezpečný přístup z více vláken.  
  
### <a name="managed-clients-and-com-servers"></a>Spravovaných klientů a serverů modelu COM  
 Výchozí nastavení pro klienta spravovaného Apartment je MTA; Typ aplikace klienta rozhraní .NET můžete však změnit výchozí nastavení. Například [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] STA je nastavení klienta objektu apartment Můžete použít <xref:System.STAThreadAttribute?displayProperty=nameWithType>, <xref:System.MTAThreadAttribute?displayProperty=nameWithType>, <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> vlastnost, nebo <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType> vlastnost sloužící ke zkoumání a změňte nastavení typu apartment spravovaného klienta.  
  
 Autor komponentu nastaví spřažení podprocesu COM serveru. V následující tabulce jsou uvedeny kombinace apartment nastavení pro rozhraní .NET klienty a servery COM. Také ukazuje výsledná zařazování požadavky pro kombinace.  
  
|Klient .NET|COM server|Zařazování požadavky|  
|-----------------|----------------|-----------------------------|  
|Protokol MTA (výchozí)|MTA<br /><br /> STA|Zařazování spolupráce<br /><br /> Zprostředkovatel komunikace s objekty a zařazování COM.|  
|STA|MTA<br /><br /> STA|Zprostředkovatel komunikace s objekty a zařazování COM.<br /><br /> Zařazování spolupráce|  
  
 Při nespravovanému serveru a klienta spravovaného jsou ve stejné typu apartment, zprostředkovatel komunikace s objekty služby zařazování zpracovává všechny zařazování data. Ale když klient a server se inicializují v různých apartment, COM zařazování je také nutný. Na následujícím obrázku je znázorněno volání mezi apartment.  
  
 ![Zařazování COM](../../../docs/framework/interop/media/singleprocessmultapt.gif "singleprocessmultapt")  
Volání mezi apartment mezi klient .NET a objekt modelu COM  
  
 Pro zařazování mezi apartment, můžete provést následující:  
  
-   Přijměte režii zařazování mezi apartment, což je patrné, jenom v případě, že existuje mnoho volání přes hranice. Je nutné zaregistrovat knihovnu typů součásti COM pro volání úspěšně překročit hranice typu apartment.  
  
-   Změnit nastavení klientské vlákno STA nebo MTA hlavního vlákna. Například pokud váš klient C# volá mnoho STA COM – součásti, se můžete vyhnout mezi apartment zařazování nastavením hlavního vlákna na STA  
  
    > [!NOTE]
    >  Vlákno klienta C# nastavenou na hodnotu STA, bude vyžadovat volání do modelu MTA COM – součásti zařazování mezi apartment.  
  
 Pokyny týkající se explicitně výběru apartment model najdete v tématu [spravovaná a nespravovaná vlákna](http://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5).  
  
 [Zpět na začátek](#top)  
  
<a name="marshaling_remote_calls"></a>   
## <a name="marshaling-remote-calls"></a>Zařazování Vzdálená volání  
 Stejně jako u mezi apartment zařazování, COM zařazování je zahrnuta v každé volání mezi spravovanými a nespravovanými kódem vždy, když se objekty nacházejí v oddělených procesech. Příklad:  
  
-   Klient COM, který volá spravovaný server na vzdálený hostitel používá distributed COM (DCOM).  
  
-   Spravovaný klient, který volá server COM na vzdáleného hostitele používá model DCOM.  
  
 Následující obrázek znázorňuje, jak spolupráce zařazování a COM zařazování zadejte komunikačních kanálů napříč hranicemi proces a hostitele.  
  
 ![Zařazování COM](../../../docs/framework/interop/media/interophost.gif "interophost")  
Zařazování mezi procesy  
  
### <a name="preserving-identity"></a>Zachování Identity  
 Modul common language runtime zachovává identitu spravovanými a nespravovanými odkazy. Následující obrázek znázorňuje tok přímé nespravované odkazy (horní řádek) a přímé odkazy na spravovaného (dolní řádek) napříč hranicemi proces a hostitele.  
  
 ![Obálka volatelná aplikacemi COM a obálka volatelná za běhu](../../../docs/framework/interop/media/interopdirectref.gif "interopdirectref")  
Odkaz na předávání přes hranice procesu a hostitele  
  
 V tomto obrázku:  
  
-   Nespravovaný klient získá odkaz na objekt COM ze spravovaného objektu, který získá odkaz na tento od vzdáleného hostitele. Tento mechanismus vzdálené komunikace je model DCOM.  
  
-   Spravovaný klient získá odkaz na objekt spravovaného z objektu COM, který získá odkaz na tento od vzdáleného hostitele. Tento mechanismus vzdálené komunikace je model DCOM.  
  
    > [!NOTE]
    >  Knihovna exportovaný typ spravovaného serveru musí být zaregistrován.  
  
 Počet proces hranice mezi volající a volaný je důležité; stejné přímé odkazujícího dochází v procesu a out-of-process volání.  
  
### <a name="managed-remoting"></a>Spravované vzdálené komunikace  
 Modul runtime také poskytuje spravované vzdálenou komunikaci, která vám pomůže vytvořit komunikační kanál mezi spravované objekty napříč hranicemi proces a hostitele. Spravované vzdálenou komunikaci zvládne brány firewall mezi součástmi komunikuje, jak ukazuje následující obrázek.  
  
 ![Protokol SOAP nebo TcpChannel](../../../docs/framework/interop/media/interopremotesoap.gif "interopremotesoap")  
Vzdálená volání přes brány firewall pomocí protokolu SOAP nebo TcpChannel – třída  
  
 Některá volání nespravovaného můžete channeled prostřednictvím protokolu SOAP, jako je například volání mezi [obsluhované komponenty](http://msdn.microsoft.com/library/f109ee24-81ad-4d99-9892-51ac6f34978c) a COM.  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Výchozí chování zařazování](../../../docs/framework/interop/default-marshaling-behavior.md)|Popisuje pravidla, která používá službu zařazování spolupráce zařazování dat.|  
|[Zařazování dat s voláním platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)|Popisuje, jak deklarace parametry metody a předání argumentů funkce exportované sadou nespravované knihovny.|  
|[Zařazování dat se spoluprací COM](../../../docs/framework/interop/marshaling-data-with-com-interop.md)|Popisuje, jak přizpůsobit COM – obálky ke změně chování zařazování.|  
|[Postup: Migrace spravovaného kódu DCOM do WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)|Popisuje, jak migrovat z modelu DCOM do WCF.|  
|[Postupy: Mapování výsledků HRESULT a výjimek](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)|Popisuje, jak namapovat vlastní výjimky pro hodnoty HRESULT a poskytuje kompletní mapování z každé HRESULT do své třídy porovnatelný z hlediska výjimek v rozhraní .NET Framework.|  
|[Spolupráce pomocí obecných typů](http://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58)|Popisuje akce, které jsou podporovány při použití obecných typů pro interoperabilita modelů COM.|  
|[Spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md)|Popisuje vzájemná funkční spolupráce služeb poskytovaných tímto modul common language runtime.|  
|[Interoperabilita modelů COM Upřesnit](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)|Obsahuje odkazy na další informace o zahrnutí komponenty modelu COM do své aplikace rozhraní .NET Framework.|  
|[Aspekty návrhu pro spolupráci](http://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689)|Poskytuje tipy pro zápis integrované COM – součásti.|  
  
 [Zpět na začátek](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.Runtime.InteropServices?displayProperty=nameWithType>  
  
 [Zpět na začátek](#top)
