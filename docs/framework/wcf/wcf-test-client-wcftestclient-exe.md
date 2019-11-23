---
title: WCF Test Client (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: ac89b234dfafe3f87f1423a04ce8e4dd6b44b991
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321179"
---
# <a name="wcf-test-client-wcftestclientexe"></a>WCF Test Client (WcfTestClient.exe)
Testovací klient Windows Communication Foundation (WCF) (WcfTestClient. exe) je nástroj grafického uživatelského rozhraní, který umožňuje uživatelům zadat parametry testu, odeslat tento vstup do služby a zobrazit odpověď, kterou služba odesílá zpět. Poskytuje bezproblémové prostředí pro testování služeb při kombinaci s hostitelem služby WCF.

Můžete obvykle najít testovacího klienta WCF (WcfTestClient. exe) v následujícím umístění: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE`-Community může být jeden z "Enterprise", "Professional" nebo "Community" v závislosti na tom, která úroveň sady Visual Studio je nainstalována.

## <a name="scenarios-for-using-test-client"></a>Scénáře použití testovacího klienta

Následující části popisují nejběžnější scénáře, ve kterých můžete použít testovacího klienta WCF k zjednodušení procesu vývoje.

### <a name="inside-visual-studio"></a>V rámci sady Visual Studio

#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>Hostitel služby WCF spustí testovacího klienta WCF s jednou službou.

Po vytvoření nového projektu služby WCF a stisknutím klávesy F5 ke spuštění ladicího programu začne hostitel služby WCF hostovat službu ve vašem projektu. Pak se klient testu WCF otevře a zobrazí seznam koncových bodů služby, které jsou definované v konfiguračním souboru. Můžete testovat parametry a vyvolat službu a opakováním tohoto procesu průběžně testovat a ověřovat vaši službu.

#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>Hostitel služby WCF spustí testovacího klienta WCF s více službami.

Můžete také použít testovacího klienta WCF pro usnadnění ladění projektu služby, který obsahuje více služeb. Když se klient služby WCF test otevře, automaticky prochází seznam služeb ve vašem projektu a otevírá je pro testování.

### <a name="outside-visual-studio"></a>Mimo Visual Studio

Můžete také vyvolat testovacího klienta WCF (WcfTestClient. exe) mimo Visual Studio k otestování libovolné služby na internetu. Chcete-li najít tento nástroj, přejděte do následujícího umístění:

`C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (kde Community může být jedna z "Enterprise", "Professional" nebo "Community" v závislosti na tom, jaká úroveň sady Visual Studio je v počítači nainstalována)

Chcete-li použít nástroj, poklikejte na název souboru a otevřete ho z tohoto umístění, nebo ho spusťte z příkazového řádku.

Testovací klient WCF bere libovolný počet identifikátorů URI jako argumenty příkazového řádku.  Jedná se o identifikátory URI služeb, které lze testovat.

`wcfTestClient.exe URI1 URI2 …`

Po otevření okna testovacího klienta WCF klikněte na **soubor**->**Přidat službu**a zadejte adresu koncového bodu služby, kterou chcete otevřít.

## <a name="wcf-test-client-user-interface"></a>Uživatelské rozhraní testovacího klienta WCF

Můžete použít testovacího klienta WCF s jednou službou nebo více službami.

### <a name="service-operations"></a>Operace služby

V levém podokně hlavního okna klienta služby WCF se zobrazí všechny dostupné služby spolu s příslušnými koncovými body a operacemi.

Po dvojitém kliknutí na operaci můžete zobrazit její obsah v pravém podokně na nové kartě s názvem operace.

V levém podokně jsou uvedeny také konfigurační soubory klienta. Dvojitým kliknutím na kteroukoli položku zobrazíte obsah souboru v novém okně s kartami v pravém podokně.

### <a name="entering-test-parameters"></a>Zadávání parametrů testu

Chcete-li zobrazit parametry testu, klikněte dvakrát na operaci a otevřete ji v pravém podokně. Parametry jsou ve výchozím nastavení zobrazeny ve **formátovaných** zobrazeních a můžete zadat libovolné hodnoty pro parametry pro otestování služby.

Pokud chcete zobrazit XML zprávy, klikněte na **XML**. Pokud je chcete odeslat službě, klikněte na **vyvolat**.

Pro parametr DataSet klikněte na. **.** tlačítko vedle **úpravy...** pro jeho úpravu v novém okně, které zobrazuje prvek DataGrid. Všimněte si, že se zobrazují tlačítka **Kopírovat datovou sadu** a **Vložit datovou sadu** . Pokud schéma objektu DataSet není po prvním úpravách známé, DataGrid je prázdné. Je nutné vložit objekt DataSet se stejným schématem do aktuálního objektu v prvku DataGrid. (Všimněte si, že před vložením je nutné zkopírovat schéma z někde jinde.) Můžete také zkopírovat objekt DataSet pro budoucí použití kliknutím na tlačítko **Kopírovat datovou sadu** .

Odpověď služby se zobrazí pod parametry testu.

> [!NOTE]
> Pokud je očekávaná návratová hodnota řetězec, výsledek se zobrazí jako řetězec v uvozovkách, i když zadaný vstup nebyl v uvozovkách.

Pokud jste při vytváření smlouvy pro službu zadali určitou operaci jako jednosměrnou, nezobrazí se žádná odpověď služby. Jakmile je zpráva zařazená do fronty pro doručení, zobrazí se dialogové okno s oznámením, že zpráva byla úspěšně odeslána.

### <a name="session-support"></a>Podpora relací

Zaškrtávací políčko **zahájit novou službu proxy** na kartě operace služby umožňuje přepnout podporu relace. Ve výchozím nastavení je toto políčko nezaškrtnuté.

Když zadáte parametry testu pro určitou operaci (nebo jinou operaci ve stejném koncovém bodu služby) a zaškrtnutím políčka **vyvoláte** několikrát, tyto operace budou sdílet jeden proxy server a stav služby je trvale v rámci více operací.

Pokud je zaškrtnuté políčko **Spustit nový proxy server** , spustí se pro každé **vyvolání**nový proxy server, předchozí scénář relace se ukončí a stav služby se resetuje.

### <a name="editing-client-configuration"></a>Úprava konfigurace klienta

V levém podokně hlavního okna klienta služby WCF je uveden seznam konfiguračních souborů klienta. Dvojitým kliknutím na kteroukoli položku zobrazíte obsah souboru v pravém podokně.

#### <a name="edit-with-service-configuration-editor"></a>Upravit pomocí editoru konfigurace služby

V levém podokně klikněte pravým tlačítkem na **konfigurační soubor** a vyberte kontextovou nabídku **upravit pomocí SvcConfigEditor**. Editor konfigurace služby se spustí s obsahem konfigurace klienta. Konfiguraci můžete upravit a uložit v rámci nástroje.

Po uložení souboru v editoru konfigurace služby zobrazí klient testu WCF zprávu s upozorněním, že se soubor změnil mimo a zeptá se, jestli byste ho chtěli znovu načíst.

Pokud vyberete **Ano**, bude obsah konfigurace na kartě Client. dll. config odpovídat změnám, které jste provedli v editoru.

Pokud vyberete **ne**, obsah konfigurace na kartě Client. dll. config zůstane beze změny a změněný obsah se automaticky uloží do zdrojového souboru.

#### <a name="restore-to-default-configuration"></a>Obnovit výchozí konfiguraci

Pokud chcete zrušit všechny změny a obnovit výchozí konfiguraci klienta, klikněte pravým tlačítkem na konfigurační **soubor** v levém podokně a vyberte kontextovou nabídku **obnovit do výchozí**konfigurace. Je načtena výchozí hodnota konfigurace a dojde k obnovení obsahu na kartě Client. dll. config.

#### <a name="validate-changes"></a>Ověřit změny

Když jsou uložené změny načítány do testovacího klienta WCF, je u konfigurace kontrolována platnost schématu WCF. Pokud dojde k chybám, zobrazí se dialogové okno, ve kterém se zobrazí podrobnosti o chybě.

Během generování proxy, binární kompilace nebo vyvolání služby jsou položky nabídky, které podporují úpravy (tj. "Edit...", "Restore..." atd.) zakázané. Při načítání aktualizované konfigurace do testovacího klienta WCF je vyvolání služby také zakázáno.

#### <a name="persist-client-configuration"></a>Trvalá konfigurace klienta

**Možnosti**->**nástroje**->kartě **Konfigurace klienta** obsahují možnost **vždy znovu generovat konfiguraci při spuštění služby** , která je ve výchozím nastavení povolená. Tato možnost určuje, že pokaždé, když klient služby WCF test nahraje službu, znovu vygeneruje konfigurační soubor na základě nejnovějšího kontraktu služby a souborů. config aplikace služby.

Pokud jste upravili konfiguraci klienta pro službu WCF a chcete tento aktualizovaný soubor vždy použít k ladění vaší služby, můžete zrušit možnost **znovu vygenerovat** . Provedete to i v případě, že aktualizujete službu a znovu otevřete testovacího klienta WCF, soubor Client. dll. config je ten, který jste předtím aktualizovali, místo aby se znovu vygeneroval na základě aktualizované služby.

Je však možné, že budete muset upravit konfigurační soubor, aby byl konzistentní s obnoveným proxy serverem. Pokud se znovu vygenerované proxy a konfigurační soubor neshodují kvůli aktualizované službě, při vyvolání služby dojde k chybám.

> [!CAUTION]
> Pokud jste změnili konfigurační soubor klienta a v budoucnu vyberete možnost ho znovu použít, můžete soubor najít v následujícím umístění:
>
> \Documents and Settings\\[uživatelský účet] \Dokumenty Documents\Test klientské projekty.
>
> Všechny aktualizované přihlašovací údaje uložené do konfiguračního souboru klienta jsou chráněny seznamem Access Control (ACL) této složky.

### <a name="adding-removing-and-refreshing-services"></a>Přidávání, odebírání a aktualizace služeb

#### <a name="add-service"></a>Add Service

Kliknutím na **soubor**->**Přidat službu** přidejte službu do testovacího klienta WCF. Pak je nutné zadat identifikátor URI (adresa koncového bodu) služby, kterou chcete přidat. Adresa služby může být adresa MEX nebo adresa WSDL.

V podnabídce **nedávné služby** můžete také vyhledat seznam koncových bodů 10 naposledy přidaných služeb. Pokud vyberete jednu z nich, bude Zadaná služba přidána do testovacího klienta WCF.

Můžete také kliknout pravým tlačítkem na kořen **projekty moje služby**stromové struktury služby a výběrem **Přidat službu** dosáhnout stejného výsledku.

Během generování proxy, binární kompilace nebo vyvolání služby jsou položky nabídky, které podporují přidávání služby, zakázané. Vyvolání služby je také zakázáno.

#### <a name="remove-service"></a>Odebrat službu

Klikněte pravým tlačítkem na kořenový adresář služby, který chcete odebrat, a vyberte **Odebrat službu** pro odebrání služby z testovacího klienta WCF.

Během generování proxy, binární kompilace nebo vyvolání služby jsou položky nabídky, které podporují odebrání služby, zakázané. Vyvolání služby je také zakázáno.

#### <a name="refresh-service"></a>Aktualizovat službu

Pokud dojde ke změně služby, zatímco je spuštěný klient služby WCF test a chcete zajistit, aby byla implementace klienta služby WCF pro tuto službu aktuální, klikněte pravým tlačítkem myši na kořenový adresář služby a vyberte možnost **aktualizovat službu**. Všimněte si, že po obnovení se stav služby resetuje.

Během generování proxy, binární kompilace nebo vyvolání služby jsou položky nabídky, které podporují aktualizaci služby, zakázané. Vyvolání služby je také zakázáno.

## <a name="location-of-files-generated-by-the-test-client"></a>Umístění souborů generovaných testovacím klientem

Ve výchozím nastavení služba WCF test Client ukládá generovaný klientský kód a konfigurační soubory do složky "klientské projekty%appdata%\Local\temp\Test". Tato složka se odstraní po ukončení klienta služby WCF test. Pokud je v testovacím klientovi služby WCF upraven konfigurační soubor a možnost **vždy znovu generovat konfiguraci při spuštění služeb** je zakázána, je upravený soubor zkopírován do složky "CachedConfig" v části "projekty klientů Documents\Test" s mapováním (metadata-adresa-soubor-název) souboru XML jako index.

Můžete také spustit testovacího klienta WCF na příkazovém řádku, použít přepínač `/ProjectPath` a zadat novou požadovanou cestu pro ukládání vygenerovaných souborů nebo použít přepínač `/RestoreProjectPath` k obnovení výchozího umístění. Syntaxe je následující:

`wcfTestClient.exe /ProjectPath [desired location]`

Spuštění tohoto příkazu neotevře testovacího klienta WCF. Změnilo se jenom umístění složky. Tento příkaz můžete spustit, pokud je spuštěný klient služby WCF test. Nové umístění se použije při restartování klienta služby WCF test. Informace o umístění mohou být uloženy v registru nebo v souboru WcfTestClient. exe. Option ve složce "projekty klientů%appdata%\Local\temp\Test".

## <a name="features-supported-by-wcf-test-client"></a>Funkce podporované testovacím klientem WCF

Následuje seznam funkcí podporovaných testovacím klientem WCF:

- Vyvolání služby: požadavek/odpověď a jednosměrná zpráva.

- Vazby: všechny vazby podporované nástrojem Svcutil. exe.

- Řízení relace.

- Kontrakt zprávy.

- Serializace XML.

Následuje seznam funkcí, které služba WCF test Client nepodporuje:

- Typy: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, typy, které implementují rozhraní <xref:System.Xml.Serialization.IXmlSerializable>, včetně souvisejícího <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributu a <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> typy a ADO.NET <xref:System.Data.DataTable> typ.

- Duplexní kontrakt.

- Transakce.

- Zabezpečení: CardSpace, certifikát a uživatelské jméno a heslo.

- Vazby: WSFederationbinding, jakékoli vazby kontextu a vazba https, WebHttpbinding (podpora zpráv odpovědí JSON).

## <a name="closing-wcf-test-client"></a>Ukončení testovacího klienta WCF

Klienta služby WCF test můžete uzavřít následujícími způsoby:

- V nabídce **soubor** klikněte na příkaz **ukončit**. Případně můžete v hlavním okně klienta služby WCF test kliknout na **Zavřít**. Obě tyto akce také ukončí automatické hostování služby WCF a zastavuje proces ladění sady Visual Studio, pokud byl spuštěn testovací klient WCF pomocí sady Visual Studio.

- Klikněte pravým tlačítkem myši na ikonu **hostitele služby WCF** v oznamovací oblasti a pak klikněte na tlačítko **konec.** Tím se vypne jak automatický hostitel služby WCF, tak i testovací klient WCF a zastaví se proces ladění sady Visual Studio.

## <a name="see-also"></a>Viz také:

- [Hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
