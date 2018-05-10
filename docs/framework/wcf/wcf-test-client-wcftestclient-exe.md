---
title: WCF Test Client (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 78be40268b46c4c85ee034db67d67ee0fbf2158f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-test-client-wcftestclientexe"></a>WCF Test Client (WcfTestClient.exe)
Testování klienta Windows Communication Foundation (WCF) (WcfTestClient.exe) je nástroj grafickým uživatelským rozhraním, který umožňuje uživatelům vstupní parametry testu, odeslat tento vstup do služby a zobrazit odpověď zpět odeslaná službě. Poskytuje bezproblémové služby testování prostředí při kombinaci s hostitel služby WCF.  
  
 Obvykle můžete najít testovacího klienta WCF (WcfTestClient.exe) v následujícím umístění: C:\Program Files (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE - komunity může mít jednu z "Podniku", "Professional" nebo "Komunit" v závislosti na kterém úroveň sady Visual Studio je nainstalována.
  
## <a name="scenarios-for-using-test-client"></a>Scénáře použití testovacího klienta  
 Následující části popisují nejběžnější scénáře, ve kterých se dá použít testovacího klienta WCF zefektivnění vývojových procesech.  
  
### <a name="inside-visual-studio"></a>Uvnitř sady Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>Služba hostitele spustí WCF testovacího klienta WCF jedinou službou  
 Po vytvoření nového projektu služby WCF a stisknutím klávesy F5 spusťte ladicí program, začne se hostitel služby WCF k hostování služby ve vašem projektu. Poté testovacího klienta WCF otevře a zobrazí seznam koncových bodů služby definována v konfiguračním souboru. Můžete otestovat parametry a vyvolání službu a opakujte tento postup nepřetržitě testování a ověření služby.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>Služba hostitele spustí WCF testovacího klienta WCF s více službami  
 Klienta WCF testu můžete taky pomáhají ladit projekt služby, který obsahuje více služeb. Když se otevře testovacího klienta WCF, automaticky opakuje seznamu služeb ve vašem projektu a je otevře pro testování.  
  
### <a name="outside-visual-studio"></a>Mimo aplikaci Visual Studio  
 Můžete také vyvolat klienta WCF Test (WcfTestClient.exe) mimo Visual Studio k testování libovolný službou na Internetu. Chcete-li vyhledat nástroj, přejděte do následujícího umístění:  
  
 C:\Program Files\Microsoft 9.0\Common7\IDE\ sady Visual Studio  
  
 Použití nástroje, klikněte dvakrát na název souboru a otevře se z tohoto umístění nebo spusťte z příkazového řádku.  
  
 Testovacího klienta WCF přebírá libovolný počet identifikátory URI jako argumenty příkazového řádku.  Jedná se o identifikátory URI služeb, které může být testována.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 Po otevření okna testovacího klienta WCF, klikněte na tlačítko **soubor**->**přidat službu**a zadejte adresa koncového bodu služby, kterou chcete otevřít.  
  
## <a name="wcf-test-client-user-interface"></a>Uživatelské rozhraní klienta testovací WCF  
 WCF testovacího klienta můžete použít se službou jeden nebo více služeb.  
  
### <a name="service-operations"></a>Operace služby  
 Levém podokně hlavního okna testovacího klienta WCF uvádí všechny dostupné služby, spolu s jejich příslušných koncových bodů a operace.  
  
 Když dvakrát kliknete na operace, můžete zobrazit jeho obsah v pravém podokně uvnitř novou kartu s názvem operace.  
  
 V levém podokně také uvádí konfigurační soubory klienta. Poklikejte na některou z položky, které chcete zobrazit obsah souboru v novém okně s kartami v pravém podokně.  
  
### <a name="entering-test-parameters"></a>Zadat parametry testu  
 Chcete-li zobrazit parametry testu, dvakrát klikněte na určité operace, otevřete v pravém podokně. Parametry jsou uvedeny v **naformátovaný** zobrazení ve výchozím nastavení, a můžete zadat libovolný hodnoty pro parametry, které chcete testovat službu.  
  
 Chcete-li zobrazit zprávy XML, klikněte na tlačítko **XML**. Je odeslat do služby, klikněte na tlačítko **Invoke**.  
  
 Parametr datové sady, klikněte na **...** vedle položky **upravit...** úpravy v novém okně zobrazující v kolekci DataGrid. Všimněte si vzhled **datovou sadu kopie** a **datovou sadu vložení** tlačítka. Pokud schéma datové sady objektu Neznámý při první úpravy, v kolekci DataGrid je prázdný. Je třeba vložit objekt datová sada se stejným schématem do aktuální objekt v objektu DataGrid. (Všimněte si, budete muset zkopírovat schéma z jinde než operaci vložení.) Můžete také zkopírovat objekt datovou sadu pro budoucí použití kliknutím **datovou sadu kopie** tlačítko.  
  
 Odpověď služby se zobrazí pod parametry testu.  
  
> [!NOTE]
>  Očekávaná návratová hodnota je řetězec, výsledek jako řetězec v uvozovkách zobrazit, i když vstup nebyl v uvozovkách.  
  
 Pokud jste zadali určité operace jako jednosměrný při vytvoření kontraktu služby, se zobrazí odpověď žádné služby. Co nejrychleji zprávy ve frontě pro doručení, dialogové okno se zobrazí oznámení, že zpráva byla úspěšně odeslána.  
  
### <a name="session-support"></a>Podpora relace  
 **Spustit nový proxy** políčko na kartě operace služby umožňuje přepínat podporu relací. Je toto políčko není ve výchozím nastavení.  
  
 Po zadání parametry testu pro konkrétní operaci (nebo jiná operace stejný koncový bod služby) a klikněte na tlačítko **Invoke** vícekrát s políčko nezaškrtnuto tyto operace sdílet jeden proxy server a je stav služby. zachová pro více operací.  
  
 Pokud **spustit nový proxy** zaškrtávací políčko je zaškrtnuto, nový proxy je spuštěno pro každou **Invoke**, scénář předchozí relace se ukončí a se vynuluje stav služby.  
  
### <a name="editing-client-configuration"></a>Úpravy konfigurace klienta  
 Levém podokně hlavního okna testovacího klienta WCF uvádí konfigurační soubory klienta. Poklikejte na některou z položky, které chcete zobrazit obsah souboru v pravém podokně.  
  
#### <a name="edit-with-service-configuration-editor"></a>Upravit pomocí editoru konfigurace služby  
 Klikněte pravým tlačítkem na **konfiguračního souboru** v levém podokně a vyberte příslušnou kontextovou nabídku **upravit SvcConfigEditor**. Editor konfigurací služba se spustí s obsahem konfigurace klienta. Můžete upravit konfiguraci a uložit ho v rámci nástroje.  
  
 Po uložení souboru v editoru konfigurace služby, WCF testovacího klienta zobrazí zprávu upozornění o tom, zda soubor byl upraven mimo a zobrazí dotaz, zda chcete znovu načíst.  
  
 Pokud vyberete **Ano**, obsah konfigurace na kartě "Client.dll.config" odráží změny provedené v editoru.  
  
 Pokud vyberete **ne**, obsah konfigurace na kartě "Client.dll.config" zůstává beze změny a automaticky je upravený obsah se uloží ke zdrojovému souboru.  
  
#### <a name="restore-to-default-configuration"></a>Obnovit výchozí konfigurace  
 Pokud chcete zrušit všechny změny a obnovit výchozí konfiguraci klienta, klikněte pravým tlačítkem na **konfiguračního souboru** v levém podokně a vyberte příslušnou kontextovou nabídku **obnovit výchozí konfigurace**. Výchozí hodnota konfigurace je načtena a obsah na kartě "Client.dll.config" je obnovit.  
  
#### <a name="validate-changes"></a>Ověřit změny  
 Při načítání uložené změny v testovacího klienta WCF, konfigurace se kontroluje na platnosti pro schéma WCF. Pokud k chybám, zobrazí se dialogové okno zobrazíte podrobnosti o chybě.  
  
 Během vytváření proxy, binární kompilování nebo volání služby, které podporují úpravy (tedy "Upravit...", "Obnovení..." atd.) nebudou k dispozici. Volání služby se vypne taky při načítání aktualizaci konfigurace na testovacího klienta WCF.  
  
#### <a name="persist-client-configuration"></a>Zachovat konfigurace klienta  
 **Nástroje**->**možnosti**->**konfigurace klienta** karta obsahuje **vždy znovu vygenerovat konfigurace při spuštění Služby** možnost, která je ve výchozím nastavení povolené. Tato možnost určuje, že pokaždé, když klienta WCF Test načte službu, regeneruje konfigurační soubor na základě nejnovější kontrakt služby a soubory App.config služby.  
  
 Pokud jste upravili konfigurace klienta služby WCF a chcete vždy použít tento aktualizovaný soubor k ladění vaší služby, můžete zrušit zaškrtnutí **znovu vygenerovat** možnost. Díky tomu i v případě, že aktualizace služby a znovu otevřete testovacího klienta WCF, soubor Client.dll.config je ten, který jste dříve aktualizaci místo znova vygeneroval jeden založené na službě aktualizované.  
  
 Chcete-li upravit konfigurační soubor, aby bylo konzistentní se znova vygeneroval proxy však může být zapotřebí. Pokud z důvodu aktualizované služby se neshodují se znova vygeneroval proxy a konfigurační soubor, dojde k chybám při vyvolání služby.  
  
> [!CAUTION]
>  Pokud byly upraveny konfiguračního souboru klienta a vyberte znovu použít v budoucnosti, můžete najít soubor v následujícím umístění:  
>   
>  \Documents and Settings\\[uživatelský účet] \My Documents\Test klientského projektu.  
>   
>  Žádné aktualizované přihlašovací údaje uložit do konfiguračního souboru klienta je chráněný pomocí ovládacího prvku seznam přístupu (ACL) této složky.  
  
### <a name="adding-removing-and-refreshing-services"></a>Přidání, odebrání a obnovení služby  
  
#### <a name="add-service"></a>Přidání služby  
 Klikněte na tlačítko **soubor**->**přidat službu** přidat službu WCF testovacího klienta. Pak musíte zadat identifikátor URI (adresa koncového bodu) služby, který se má přidat. Adresa služby může být mex adres nebo adres WSDL.  
  
 Můžete také získat seznam koncových bodů 10 nedávno přidané služeb v **poslední služby** podnabídky. Pokud vyberete jednu z nich, určenou službu se přidá do testovacího klienta WCF.  
  
 Můžete také kliknout pravým tlačítkem kořenu stromu služby **Moje projekty služeb**a vyberte **přidat službu** k dosažení stejného výsledku.  
  
 Během proxy generace, binární kompilování nebo volání služby, které podporují přidání služby nebudou k dispozici. Volání služby se vypne taky.  
  
#### <a name="remove-service"></a>Odebrání služby  
 Klikněte pravým tlačítkem na kořenový adresář služby odeberou a vyberte **odebrat služby** k odebrání služby WCF testovacího klienta.  
  
 Během proxy generace, binární kompilování nebo volání služby, které podporují odebrání služby nebudou k dispozici. Volání služby se vypne taky.  
  
#### <a name="refresh-service"></a>Aktualizace služby  
 Pokud dojde ke změně ke službě WCF testovacího klienta běží a chcete zajistit, že je aktuální implementace testovacího klienta WCF pro tuto službu, klikněte pravým tlačítkem na kořenový adresář služby a vyberte **aktualizace služby**. Všimněte si, že po obnovení, stav služby se vynuluje.  
  
 Během proxy generace, binární kompilování nebo volání služby, které podporují aktualizace služby nebudou k dispozici. Volání služby se vypne taky.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Umístění souborů generované testovacího klienta  
 Ve výchozím nastavení ukládá testovacího klienta WCF generována soubory kódu a konfigurace klienta ve složce "%appdata%\Local\temp\Test projekty klienta". Tato složka je odstranit po ukončení klienta WCF Test. Pokud je konfigurační soubor upravovat v testovacího klienta WCF a **vždy znovu vygenerovat konfigurace při spuštění služby** možnost je vypnuta, změněný soubor zkopírován do složky "Konfigurace uložené v mezipaměti" v "Moje Documents\Test klientského projektu Projekty klienta Documents\Test"se souborem XML mapování (metadata adresy do souboru – název) jako index.  
  
 Můžete také spustit Test klienta WCF v příkazovém řádku, použijte `/ProjectPath` přejděte na zadat novou požadovanou cestu pro ukládání generovaného souborů, nebo použijte `/RestoreProjectPath` přepínač tak, aby obnovit výchozí umístění. Syntaxe vypadá takto:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 Spuštění tohoto příkazu se neotevře testovacího klienta WCF. Umístění složky se změní. Tento příkaz můžete spustit, zda je spuštěný klient testovací WCF, nebo ne. Nové umístění se použije při restartování testovacího klienta WCF. Informace o umístění můžete uložit do registru nebo WcfTestClient.exe.option soubor ve složce "%appdata%\Local\temp\Test projekty klienta".  
  
## <a name="features-supported-by-wcf-test-client"></a>Funkcí podporovaných testovacího klienta WCF  
 Následuje seznam funkcí podporovaných testovacího klienta WCF:  
  
-   Volání služby: Požadavků a odpovědí a jednosměrné zprávy.  
  
-   Vazby: nepodporuje Svcutil.exe všechny vazby.  
  
-   Řízení relace.  
  
-   Kontrakt zprávy.  
  
-   Serializace XML.  
  
 Následuje seznam funkcí nepodporuje testovacího klienta WCF:  
  
-   Typy: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, které implementují typy <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, včetně související <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atribut a <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> typy a technologie ADO.NET <xref:System.Data.DataTable> typu.  
  
-   Duplexní kontrakt.  
  
-   Transakce.  
  
-   Zabezpečení: [!INCLUDE[infocard](../../../includes/infocard-md.md)] , certifikátu a uživatelského jména a hesla.  
  
-   Vazby: Wsfederationbinding –, všechny kontextu vazby a vazbu Https, WebHttpbinding (podporu zprávu odpovědi Json).  
  
## <a name="closing-wcf-test-client"></a>Zavřením testovacího klienta WCF  
 Testovacího klienta WCF můžete zavřít následujícími způsoby:  
  
-   Na **soubor** nabídky, klikněte na tlačítko **ukončení**. Můžete taky v hlavním okně testovacího klienta WCF, klikněte na tlačítko **Zavřít**. Jak z těchto akcí také vypnout automatické hostitel služby WCF a zastavte ladění proces sady Visual Studio, pokud byl spuštěn Test klienta WCF Visual Studio.  
  
-   Klikněte pravým tlačítkem myši **hostitel služby WCF** v oznamovací oblasti a pak klikněte na ikonu **ukončení.** Tím se vypne automatické hostitel služby WCF a testovacího klienta WCF a zastaví ladění proces sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
