---
title: WCF Test Client (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: cd6f0d7a98ca5bc5f6bee45ad296341a5b91b2a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106766"
---
# <a name="wcf-test-client-wcftestclientexe"></a>WCF Test Client (WcfTestClient.exe)
Windows Communication Foundation (WCF) testovacího klienta (WcfTestClient.exe) je nástroj grafického uživatelského rozhraní, který umožňuje uživatelům vstupní parametry testu, odeslat tento vstup do služby a zobrazovat odpovědi, které služba odesílá zpět. Poskytuje bezproblémové službu testování prostředí v kombinaci s hostitel služby WCF.  
  
 Testovací klient WCF (WcfTestClient.exe) lze obvykle najdete v následujícím umístění: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` – Community může být jedna z "Enterprise", "Professional" nebo "Komunity" v závislosti na tom, jaké úroveň sady Visual Studio je nainstalována.
  
## <a name="scenarios-for-using-test-client"></a>Scénáře použití testovacího klienta  
 Následující části popisují nejběžnějších scénářů, ve kterých můžete použít klienta testu WCF pro zjednodušení procesu vývoje.  
  
### <a name="inside-visual-studio"></a>Inside Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>WCF služby Hostitel spustí testovací klient WCF s jednou službou  
 Po vytvoření nového projektu služby WCF a stiskněte klávesu F5 ke spuštění ladicího programu, začne hostitel služby WCF hostování služby ve vašem projektu. Testovací klient WCF pak otevře a zobrazí seznam koncových bodů služby, které jsou definovány v konfiguračním souboru. Můžete testovat parametry a vyvolat službu a opakujte tento postup a průběžné testování a ověřování služby.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>WCF služby Hostitel spustí testovací klient WCF s více službami  
 Testovací klient WCF můžete také pomáhají ladit projekt služby, který obsahuje několik služeb. Po otevření testovací klient WCF automaticky iteruje seznam služeb ve vašem projektu a otevře jej pro účely testování.  
  
### <a name="outside-visual-studio"></a>Mimo sadu Visual Studio  
 Můžete také vyvolat klienta testu WCF (WcfTestClient.exe) mimo sadu Visual Studio k otestování libovolné služby na Internetu. Najít nástroj, přejděte do následujícího umístění:  
  
 `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (kde community může být jedna z "Enterprise", "Professional" nebo "Community" podle toho, která je na počítači nainstalovaný úroveň sady Visual Studio)
  
 Chcete-li použít nástroj, dvakrát klikněte na název souboru, otevřete z tohoto umístění nebo spusťte z příkazového řádku.  
  
 Testovací klient WCF přijímá libovolný počet identifikátorů URI jako argumenty příkazového řádku.  Jedná se o identifikátory URI služby, které můžete otestovat.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 Po otevření okna Testovací klient WCF, klikněte na tlačítko **souboru**->**přidat službu**a zadejte adresu koncového bodu služby, kterou chcete otevřít.  
  
## <a name="wcf-test-client-user-interface"></a>Uživatelské rozhraní klienta testu WCF  
 Můžete použít testovací klient WCF s jednou službou nebo více služeb.  
  
### <a name="service-operations"></a>Operace služby  
 Levém podokně hlavního okna Testovací klient WCF obsahuje seznam všech dostupných služeb, spolu s jejich příslušných koncových bodů a operace.  
  
 Když dvakrát kliknete na operace, můžete zobrazit jeho obsah v pravém podokně uvnitř nová karta s názvem operace.  
  
 V levém podokně jsou také uvedeny konfiguračních souborů klienta. Poklikat na kterýkoliv ze položky, které chcete zobrazit obsah souboru v novém okně s kartami v pravém podokně.  
  
### <a name="entering-test-parameters"></a>Zadat parametry testu  
 Chcete-li zobrazit parametry testu, dvakrát klikněte na operace a otevře se v pravém podokně. Parametry jsou uvedeny v **formátu** zobrazení ve výchozím nastavení, a můžete zadat libovolný hodnoty pro parametry k otestování služby.  
  
 Chcete-li zobrazit zprávy XML, klikněte na tlačítko **XML**. Aby jim odeslala do služby, klikněte na tlačítko **Invoke**.  
  
 Parametr datové sady, klikněte na tlačítko **...** vedle **upravit...** Chcete-li upravit ho v novém okně zobrazení mřížky DataGrid. Všimněte si, že vzhled **datovou sadu kopírování** a **vložit datovou sadu** tlačítka. Pokud není znám po první úpravy schématu objektu DataSet, ovládací prvek DataGrid je prázdný. Je nutné vložit objekt datové sady se stejným schématem do aktuálního objektu v mřížce DataGrid. (Všimněte si, že je potřeba zkopírovat schéma z někde jinde před provedením operace vložení.) Můžete také zkopírovat objekt datové sady pro budoucí použití kliknutím **kopírovat datovou sadu** tlačítko.  
  
 Odpověď služby se zobrazí pod parametry testu.  
  
> [!NOTE]
>  Pokud očekávané návratová hodnota je řetězec, výsledek bude zobrazen jako řetězec v uvozovkách i v případě, že vstup nebyla v uvozovkách.  
  
 Pokud jste určili konkrétní operace jako jednosměrná při vytvoření kontraktu služby, se zobrazí odpověď žádné služby. Jakmile zprávu do fronty pro doručení, dialogové okno zobrazí s upozorněním, že zpráva byla úspěšně odeslána.  
  
### <a name="session-support"></a>Podpora relace  
 **Spustit nový proxy server** zaškrtávací políčko na kartě operace služby umožňuje přepnout podporu relací. Ve výchozím nastavení se toto políčko zaškrtnuto.  
  
 Po zadání parametry testu pro konkrétní operaci (nebo jiná operace stejný koncový bod služby) a klikněte na tlačítko **Invoke** více než jednou zaškrtávací políčko zaškrtnuto, tyto operace sdílí jeden proxy server a je stav služby trvalé napříč více operacemi.  
  
 Pokud **spustit nový proxy server** zaškrtávací políčko zaškrtnuto, je spustit nový proxy server pro každou **Invoke**, scénář předchozí relace se ukončí a obnovit stav služby.  
  
### <a name="editing-client-configuration"></a>Úprava konfigurace klienta  
 Levém podokně hlavního okna Testovací klient WCF obsahuje seznam konfiguračních souborů klienta. Poklikat na kterýkoliv ze položky, které chcete zobrazit obsah souboru v pravém podokně.  
  
#### <a name="edit-with-service-configuration-editor"></a>Upravit pomocí editoru konfigurace služby  
 Klikněte pravým tlačítkem na **konfiguračního souboru** v levém podokně a vyberte v místní nabídce **upravit v editoru konfigurace služby**. Editor konfigurace služby se spustí s obsahem konfigurace klienta. Můžete upravit konfiguraci a uložit ho v rámci nástroje.  
  
 Po uložení souboru Editor konfigurace služby, se zobrazí zprávu s upozorněním a zobrazí informaci o soubor byl změněn mimo a zeptá, jestli chcete jej znovu načíst testovací klient WCF.  
  
 Pokud vyberete **Ano**, obsah konfigurace na kartě "Soubor Client.dll.config" odráží změny provedené v editoru.  
  
 Pokud vyberete **ne**, obsah konfigurace na kartě "Soubor Client.dll.config" zůstane beze změny a upravený obsah se automaticky uloží do zdrojového souboru.  
  
#### <a name="restore-to-default-configuration"></a>Obnovit výchozí konfiguraci  
 Pokud chcete zrušit všechny změny a obnovit výchozí konfiguraci klienta, klikněte pravým tlačítkem na **konfiguračního souboru** v levém podokně a vyberte v místní nabídce **obnovit výchozí nastavení**. Výchozí hodnota konfigurace je načten a obnovit obsah na kartě "Soubor Client.dll.config".  
  
#### <a name="validate-changes"></a>Ověření změn  
 Při načítání uložené změny v testovací klient WCF, konfigurace se kontroluje platnost proti schéma služby WCF. Pokud byly zjištěny chyby, zobrazí se dialogové okno zobrazíte podrobnosti o chybě.  
  
 Během generování proxy, binární kompilace nebo vyvolání služby jsou zakázané položky nabídky, které podporují úpravy (tedy "Upravit...", "Obnovit..." a tak dále). Volání služby se vypne taky při načítání aktualizaci konfigurace na testovací klient WCF.  
  
#### <a name="persist-client-configuration"></a>Zachovat konfigurace klienta  
 **Nástroje**->**možnosti**->**konfigurace klienta** karta obsahuje **vždy znovu vygenerovat konfigurace při spuštění Služby** možnost, která je ve výchozím nastavení povolené. Tato možnost určuje, že pokaždé, když se testovací klient WCF načte službu, generuje konfigurační soubor na základě nejnovější smlouvy o poskytování služeb a soubory App.config služby.  
  
 Pokud jste upravili konfigurace klienta pro vaši službu WCF a chcete vždy použít tento aktualizovaný soubor k ladění služby, můžete zrušit zaškrtnutí **znovu vygenerovat** možnost. Díky tomu i v případě, že aktualizace služby a znovu otevřete testovací klient WCF, soubor Client.dll.config souboru je ta, kterou jste aktualizovali dříve místo znovu vygenerovalo jeden založené na službě aktualizované.  
  
 Ale budete muset upravit konfigurační soubor, aby byly konzistentní s znovu vygenerovalo proxy serveru. Pokud se znovu vygenerovalo proxy serveru a konfiguračního souboru se neshodují z důvodu aktualizace služby, dojde k chybám při vyvolání služby.  
  
> [!CAUTION]
>  Pokud byly upraveny klienta konfigurační soubor a vyberte pro opětovné použití v budoucnu, můžete najít soubor v následujícím umístění:  
>   
>  Nastavení a \Documents\\[uživatelský účet] \My Documents\Test klientské projekty.  
>   
>  Žádné aktualizované přihlašovací údaje uloženy do souboru konfigurace klienta je chráněný pomocí ovládacího prvku seznam přístupu (ACL) této složky.  
  
### <a name="adding-removing-and-refreshing-services"></a>Přidání, odebrání a obnovení služby  
  
#### <a name="add-service"></a>Add Service  
 Klikněte na tlačítko **souboru**->**přidat službu** k přidání služby testovací klient WCF. Pak musíte zadejte identifikátor URI (adresa koncového bodu) služby mají být přidány. Adresa služby může být adresa mex nebo WSDL adresu.  
  
 Můžete také vyhledat seznam 10 naposledy přidané služeb koncových bodů v **poslední služby** podnabídka. Pokud vyberete jednu z nich, se přidá zadanou službu do testovací klient WCF.  
  
 Můžete také kliknout pravým tlačítkem kořen stromu služby **Moje projekty služeb**a vyberte **přidat službu** k dosažení stejného výsledku.  
  
 Během proxy generování, binární kompilace nebo vyvolání služby, které podporují přidání služby nebudou k dispozici. Volání služby se vypne taky.  
  
#### <a name="remove-service"></a>Odebrat službu  
 Klikněte pravým tlačítkem na kořenový adresář služby, které chcete odebrat, vyberte **odebrat službu** k odebrání služby testovací klient WCF.  
  
 Během proxy generování, binární kompilace nebo vyvolání služby, které podporují odebírání služby nebudou k dispozici. Volání služby se vypne taky.  
  
#### <a name="refresh-service"></a>Aktualizace služby  
 Pokud služba je provedena změna, je spuštěn testovací klient WCF a chcete mít jistotu, že je aktuální implementace klienta testu WCF pro tuto službu, klikněte pravým tlačítkem na kořenový adresář služby a vyberte **aktualizovat službu**. Všimněte si, že po aktualizaci, stav služby je obnovit.  
  
 Během proxy serveru jsou zakázána. generace, binární kompilace nebo vyvolání služby položek nabídky, které podporují aktualizaci služby. Volání služby se vypne taky.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Umístění souborů generovaných testovacího klienta  
 Ve výchozím nastavení generovány testovací klient WCF úložišť kódu a konfiguračních souborů klienta ve složce "%appdata%\Local\temp\Test klientské projekty". Tato složka je odstraněn po ukončení klienta testu WCF. Pokud je testovací klient WCF upravením konfiguračního souboru a **vždy znovu vygenerovat konfigurace při spouštění služby** možnost je vypnuta, upravený soubor je zkopírován do složky "CachedConfig" v části "Documents\Test klientské projekty" mapování souboru XML (metadata adresa na název souboru-) jako index.  
  
 Můžete také spustit klienta testu WCF v příkazovém řádku, použijte `/ProjectPath` přepnout na zadat novou požadovanou cestu pro ukládání generovaných souborů, nebo použít `/RestoreProjectPath` přepnout na výchozí umístění pro obnovení. Syntaxe vypadá takto:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 Spuštění tohoto příkazu se neotevře testovací klient WCF. Umístění složky se změní. Tento příkaz spustíte, zda testovací klient WCF běží, nebo ne. Nové umístění se používá při restartování testovacího klienta WCF. Informace o umístění můžete uložit v registru, nebo v souboru WcfTestClient.exe.option ve složce "%appdata%\Local\temp\Test klientské projekty".  
  
## <a name="features-supported-by-wcf-test-client"></a>Testovací klient WCF nepodporuje funkce  
 Následuje seznam funkcí podporovaných testovací klient WCF:  
  
-   Vyvolání služby: Žádost/odpověď a jednosměrná zpráva.  
  
-   Vazby: podporuje Svcutil.exe všechny vazby.  
  
-   Řízení relace.  
  
-   Kontrakt zprávy.  
  
-   Serializace XML.  
  
 Následuje seznam funkcí, Testovací klient WCF nepodporuje:  
  
-   Typy: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, včetně související <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atribut a <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> typy a ADO.NET <xref:System.Data.DataTable> typu.  
  
-   Duplexní kontrakt.  
  
-   Transakce.  
  
-   Zabezpečení: [!INCLUDE[infocard](../../../includes/infocard-md.md)] , certifikátu a uživatelského jména a hesla.  
  
-   Vazby: Wsfederationbinding – všechny kontextu vazby a vazbu Https, WebHttpbinding (podpora zprávu odpovědi Json).  
  
## <a name="closing-wcf-test-client"></a>Zavření testovací klient WCF  
 Testovací klient WCF můžete zavřít následujícími způsoby:  
  
-   Na **souboru** nabídky, klikněte na tlačítko **ukončovací**. Pokud v hlavním okně testovací klient WCF, klikněte na **Zavřít**. Jak z těchto akcí také vypnout automatické hostitel služby WCF a Zastavit ladění procesu Visual Studio, pokud testovací klient WCF byla spuštěna sada Visual Studio.  
  
-   Klikněte pravým tlačítkem myši **hostitel služby WCF** ikonu v oznamovací oblasti a pak klikněte na tlačítko **ukončení.** Toto vypnutí automatického hostitele služby WCF a testovací klient WCF a zastaví ladění procesu Visual Studio.  
  
## <a name="see-also"></a>Viz také:

- [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
