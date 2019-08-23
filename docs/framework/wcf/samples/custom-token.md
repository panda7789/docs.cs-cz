---
title: Vlastní token
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: 7203b55b01f51851fa94fedc4950a05343b792bd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953581"
---
# <a name="custom-token"></a>Vlastní token
Tento příklad ukazuje, jak přidat vlastní implementaci tokenu do aplikace Windows Communication Foundation (WCF). V příkladu se používá `CreditCardToken` k zabezpečenému předávání informací o kreditních kartách klienta ke službě. Token se předává v hlavičce zprávy WS-Security a je podepsaný a zašifrovaný pomocí elementu symetrického vazby zabezpečení spolu s textem zprávy a dalšími záhlavími zpráv. To je užitečné v případech, kdy vestavěné tokeny nejsou dostatečné. Tato ukázka předvádí, jak zadat vlastní token zabezpečení pro službu namísto použití jednoho z vestavěných tokenů. Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

 Pro Shrnutí Tato ukázka demonstruje následující:

- Jak může klient předat službě vlastní token zabezpečení.

- Jak může služba spotřebovávat a ověřit vlastní token zabezpečení.

- Jak může kód služby WCF získat informace o přijatých tokenech zabezpečení včetně vlastního tokenu zabezpečení.

- Způsob, jakým se používá certifikát X. 509 serveru k ochraně symetrického klíče použitého pro šifrování a podpis zprávy.

## <a name="client-authentication-using-a-custom-security-token"></a>Ověřování klientů pomocí vlastního tokenu zabezpečení
 Služba zpřístupňuje jeden koncový bod, který je programově vytvořen `BindingHelper` pomocí `EchoServiceHost` tříd a. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s vlastní vazbou pomocí `SymmetricSecurityBindingElement` a. `HttpTransportBindingElement` Tato ukázka nastaví, `SymmetricSecurityBindingElement` aby používala certifikát X. 509 služby k ochraně symetrického klíče během přenosu a aby předával vlastní `CreditCardToken` zprávu v hlavičce zprávy WS-Security jako podepsaný a zašifrovaný token zabezpečení. Chování Určuje pověření služby, které se má použít pro ověřování klientů a také informace o certifikátu služby X. 509.

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        SymmetricSecurityBindingElement messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 Pro použití tokenu platební karty ve zprávě používá ukázka k poskytnutí této funkce vlastní přihlašovací údaje služby. Třída pověření služby je umístěna ve `CreditCardServiceCredentials` třídě a je přidána do kolekce chování hostitele služby `EchoServiceHost.InitializeRuntime` v metodě.

```csharp
class EchoServiceHost : ServiceHost
{
    string creditCardFile;

    public EchoServiceHost(parameters Uri[] addresses)
        : base(typeof(EchoService), addresses)
    {
        creditCardFile = ConfigurationManager.AppSettings["creditCardFile"];
        if (string.IsNullOrEmpty(creditCardFile))
        {
            throw new ConfigurationErrorsException("creditCardFile not specified in service config");
        }

        creditCardFile = String.Format("{0}\\{1}", System.Web.Hosting.HostingEnvironment.ApplicationPhysicalPath, creditCardFile);
    }

    override protected void InitializeRuntime()
    {
        // Create a credit card service credentials and add it to the behaviors.
        CreditCardServiceCredentials serviceCredentials = new CreditCardServiceCredentials(this.creditCardFile);
        serviceCredentials.ServiceCertificate.SetCertificate("CN=localhost", StoreLocation.LocalMachine, StoreName.My);
        this.Description.Behaviors.Remove((typeof(ServiceCredentials)));
        this.Description.Behaviors.Add(serviceCredentials);

        // Register a credit card binding for the endpoint.
        Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
        this.AddServiceEndpoint(typeof(IEchoService), creditCardBinding, string.Empty);

        base.InitializeRuntime();
    }
}
```

 Koncový bod klienta je nakonfigurován podobným způsobem jako koncový bod služby. Klient používá stejnou `BindingHelper` třídu k vytvoření vazby. Zbývající část instalace je umístěna ve `Client` třídě. Klient také nastaví informace, které mají být obsaženy v `CreditCardToken` , a informace o certifikátu X. 509 v instalačním kódu `CreditCardClientCredentials` přidáním instance se správnými daty do kolekce chování koncového bodu klienta. Ukázka používá certifikát X. 509 s názvem subjektu nastaveným na `CN=localhost` jako certifikát služby.

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
EndpointAddress serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// configure the credit card credentials on the channel factory
CreditCardClientCredentials credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// configure the service certificate on the credentials
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// replace ClientCredentials with CreditCardClientCredentials
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine("Echo service returned: {0}", client.Echo());

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a>Implementace vlastního tokenu zabezpečení
 Chcete-li ve službě WCF povolit vlastní token zabezpečení, vytvořte reprezentaci objektu vlastního tokenu zabezpečení. Vzorek má toto vyjádření ve `CreditCardToken` třídě. Reprezentace objektu zodpovídá za uchovávání všech relevantních informací o tokenech zabezpečení a poskytuje seznam klíčů zabezpečení obsažených v tokenu zabezpečení. V takovém případě token zabezpečení platební karty neobsahuje žádný bezpečnostní klíč.

 V další části se dozvíte, co je potřeba udělat, abyste mohli přenést vlastní token přes kabel a spotřebovat ho pomocí koncového bodu WCF.

```csharp
class CreditCardToken : SecurityToken
{
    CreditCardInfo cardInfo;
    DateTime effectiveTime = DateTime.UtcNow;
    string id;
    ReadOnlyCollection<SecurityKey> securityKeys;

    public CreditCardToken(CreditCardInfo cardInfo) : this(cardInfo, Guid.NewGuid().ToString()) { }

    public CreditCardToken(CreditCardInfo cardInfo, string id)
    {
        if (cardInfo == null)
            throw new ArgumentNullException("cardInfo");

        if (id == null)
            throw new ArgumentNullException("id");

        this.cardInfo = cardInfo;
        this.id = id;

        // The credit card token is not capable of any cryptography.
        this.securityKeys = new ReadOnlyCollection<SecurityKey>(new List<SecurityKey>());
    }

    public CreditCardInfo CardInfo { get { return this.cardInfo; } }

    public override ReadOnlyCollection<SecurityKey> SecurityKeys { get { return this.securityKeys; } }

    public override DateTime ValidFrom { get { return this.effectiveTime; } }
    public override DateTime ValidTo { get { return this.cardInfo.ExpirationDate; } }
    public override string Id { get { return this.id; } }
}
```

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>Získání vlastního tokenu platební karty do a ze zprávy
 Serializátory tokenů zabezpečení ve službě WCF zodpovídají za vytvoření objektu reprezentace tokenů zabezpečení z XML ve zprávě a vytvoření formuláře XML tokenů zabezpečení. Jsou také zodpovědné za jiné funkce, jako je čtení a zápis identifikátorů klíčů odkazujících na tokeny zabezpečení, ale v tomto příkladu se používá pouze funkce související s tokenem zabezpečení. Pokud chcete povolit vlastní token, musíte implementovat vlastní serializátor tokenů zabezpečení. Tato ukázka používá `CreditCardSecurityTokenSerializer` třídu pro tento účel.

 Ve službě vlastní serializátor přečte formulář XML vlastního tokenu a vytvoří z něj reprezentaci objektu vlastního tokenu.

 V klientovi `CreditCardSecurityTokenSerializer` třída zapisuje informace obsažené v objektu tokenu zabezpečení reprezentaci do zapisovače XML.

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null) throw new ArgumentNullException("reader");

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null) throw new ArgumentNullException("reader");

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
        {
            string id = reader.GetAttribute(Constants.Id, Constants.WsUtilityNamespace);

            reader.ReadStartElement();

            // Read the credit card number.
            string creditCardNumber = reader.ReadElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace);

            // Read the expiration date.
            string expirationTimeString = reader.ReadElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace);
            DateTime expirationTime = XmlConvert.ToDateTime(expirationTimeString, XmlDateTimeSerializationMode.Utc);

            // Read the issuer of the credit card.
            string creditCardIssuer = reader.ReadElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace);
            reader.ReadEndElement();

            CreditCardInfo cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

            return new CreditCardToken(cardInfo, id);
        }
        else
        {
            return WSSecurityTokenSerializer.DefaultInstance.ReadToken(reader, tokenResolver);
        }
    }

    protected override bool CanWriteTokenCore(SecurityToken token)
    {
        if (token is CreditCardToken)
            return true;

        else
            return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null) { throw new ArgumentNullException("writer"); }
        if (token == null) { throw new ArgumentNullException("token"); }

        CreditCardToken c = token as CreditCardToken;
        if (c != null)
        {
            writer.WriteStartElement(Constants.CreditCardTokenPrefix, Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace);
            writer.WriteAttributeString(Constants.WsUtilityPrefix, Constants.Id, Constants.WsUtilityNamespace, token.Id);
            writer.WriteElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardNumber);
            writer.WriteElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace, XmlConvert.ToString(c.CardInfo.ExpirationDate, XmlDateTimeSerializationMode.Utc));
            writer.WriteElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardIssuer);
            writer.WriteEndElement();
            writer.Flush();
        }
        else
        {
            base.WriteTokenCore(writer, token);
        }
    }
}
```

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>Jak se vytvářejí třídy zprostředkovatele a ověřovatele ověřovacích dat tokenů
 Pověření klienta a služby jsou zodpovědná za poskytování instance Správce tokenů zabezpečení. Instance Správce tokenů zabezpečení se používá k získání poskytovatelů tokenů, ověřovatelů tokenů a serializátorů tokenů.

 Poskytovatel tokenů vytvoří objektovou reprezentaci tokenu na základě informací obsažených v pověření klienta nebo služby. Reprezentace objektu tokenu je pak zapsána do zprávy pomocí serializátoru tokenů (popsaných v předchozí části).

 Ověřovací data tokenu ověřují tokeny, které dorazí do zprávy. Reprezentace objektu příchozího tokenu je vytvořena serializátorem tokenu. Tato reprezentace objektu je pak předána ověřovateli tokenu k ověření. Po úspěšném ověření tokenu vrátí ověřovatel token kolekci `IAuthorizationPolicy` objektů, které reprezentují informace obsažené v tokenu. Tyto informace se používají později během zpracování zprávy k provedení autorizačních rozhodnutí a k poskytování deklarací identity pro aplikaci. V tomto příkladu používá `CreditCardTokenAuthorizationPolicy` ověřovací data tokenu kreditní karty k tomuto účelu.

 Serializátor tokenu zodpovídá za získání reprezentace objektu tokenu do a z tohoto drátu. Tento popis je popsaný v předchozí části.

 V této ukázce používáme poskytovatele tokenů pouze v klientech a ověřovateli tokenů pouze ve službě, protože chceme přenést token kreditní karty pouze ve směru od klienta do služby.

 Funkce klienta se nachází v `CreditCardClientCredentials` `CreditCardClientCredentialsSecurityTokenManager` třídách a `CreditCardTokenProvider` .

 Ve službě se funkce `CreditCardServiceCredentials`nachází v třídách `CreditCardTokenAuthenticator` , `CreditCardServiceCredentialsSecurityTokenManager`a `CreditCardTokenAuthorizationPolicy` .

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException("creditCardInfo");

            this.creditCardInfo = creditCardInfo;
        }

        public CreditCardInfo CreditCardInfo
        {
            get { return this.creditCardInfo; }
        }

        protected override ClientCredentials CloneCore()
        {
            return new CreditCardClientCredentials(this.creditCardInfo);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardClientCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardClientCredentialsSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        CreditCardClientCredentials creditCardClientCredentials;

        public CreditCardClientCredentialsSecurityTokenManager(CreditCardClientCredentials creditCardClientCredentials)
            : base (creditCardClientCredentials)
        {
            this.creditCardClientCredentials = creditCardClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // handle this token for Custom
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // return server cert
            else if (tokenRequirement is InitiatorServiceModelSecurityTokenRequirement)
            {
                if (tokenRequirement.TokenType == SecurityTokenTypes.X509Certificate)
                {
                    return new X509SecurityTokenProvider(creditCardClientCredentials.ServiceCertificate.DefaultCertificate);
                }
            }

            return base.CreateSecurityTokenProvider(tokenRequirement);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {

            return new CreditCardSecurityTokenSerializer(version);
        }

    }

    class CreditCardTokenProvider : SecurityTokenProvider
    {
        CreditCardInfo creditCardInfo;

        public CreditCardTokenProvider(CreditCardInfo creditCardInfo) : base()
        {
            if (creditCardInfo == null)
            {
                throw new ArgumentNullException("creditCardInfo");
            }
            this.creditCardInfo = creditCardInfo;
        }

        protected override SecurityToken GetTokenCore(TimeSpan timeout)
        {
            SecurityToken result = new CreditCardToken(this.creditCardInfo);
            return result;
        }
    }

    public class CreditCardServiceCredentials : ServiceCredentials
    {
        string creditCardFile;

        public CreditCardServiceCredentials(string creditCardFile)
            : base()
        {
            if (creditCardFile == null)
                throw new ArgumentNullException("creditCardFile");

            this.creditCardFile = creditCardFile;
        }

        public string CreditCardDataFile
        {
            get { return this.creditCardFile; }
        }

        protected override ServiceCredentials CloneCore()
        {
            return new CreditCardServiceCredentials(this.creditCardFile);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardServiceCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardServiceCredentialsSecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        CreditCardServiceCredentials creditCardServiceCredentials;

        public CreditCardServiceCredentialsSecurityTokenManager(CreditCardServiceCredentials creditCardServiceCredentials)
            : base(creditCardServiceCredentials)
        {
            this.creditCardServiceCredentials = creditCardServiceCredentials;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
            {
                outOfBandTokenResolver = null;
                return new CreditCardTokenAuthenticator(creditCardServiceCredentials.CreditCardDataFile);
            }

            return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {
            return new CreditCardSecurityTokenSerializer(version);
        }
    }

    class CreditCardTokenAuthenticator : SecurityTokenAuthenticator
    {
        string creditCardsFile;
        public CreditCardTokenAuthenticator(string creditCardsFile)
        {
            this.creditCardsFile = creditCardsFile;
        }

        protected override bool CanValidateTokenCore(SecurityToken token)
        {
            return (token is CreditCardToken);
        }

        protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateTokenCore(SecurityToken token)
        {
            CreditCardToken creditCardToken = token as CreditCardToken;

            if (creditCardToken.CardInfo.ExpirationDate < DateTime.UtcNow)
                throw new SecurityTokenValidationException("The credit card has expired");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            DefaultClaimSet cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            DefaultClaimSet cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
            policies.Add(new CreditCardTokenAuthorizationPolicy(cardClaimSet));
            return policies.AsReadOnly();
        }

        /// <summary>
        /// Helper method to check if a given credit card entry is present in the User DB
        /// </summary>
        private bool IsCardNumberAndExpirationValid(CreditCardInfo cardInfo)
        {
            try
            {
                using (StreamReader myStreamReader = new StreamReader(this.creditCardsFile))
                {
                    string line = "";
                    while ((line = myStreamReader.ReadLine()) != null)
                    {
                        string[] splitEntry = line.Split('#');
                        if (splitEntry[0] == cardInfo.CardNumber)
                        {
                            string expirationDateString = splitEntry[1].Trim();
                            DateTime expirationDateOnFile = DateTime.Parse(expirationDateString, System.Globalization.DateTimeFormatInfo.InvariantInfo, System.Globalization.DateTimeStyles.AdjustToUniversal);
                            if (cardInfo.ExpirationDate == expirationDateOnFile)
                            {
                                string issuer = splitEntry[2];
                                return issuer.Equals(cardInfo.CardIssuer, StringComparison.InvariantCultureIgnoreCase);
                            }
                            else
                            {
                                return false;
                            }
                        }
                    }
                    return false;
                }
            }
            catch (Exception e)
            {
                throw new Exception("BookStoreService: Error while retrieving credit card information from User DB " + e.ToString());
            }
        }
    }

    public class CreditCardTokenAuthorizationPolicy : IAuthorizationPolicy
    {
        string id;
        ClaimSet issuer;
        IEnumerable<ClaimSet> issuedClaimSets;

        public CreditCardTokenAuthorizationPolicy(ClaimSet issuedClaims)
        {
            if (issuedClaims == null)
                throw new ArgumentNullException("issuedClaims");
            this.issuer = issuedClaims.Issuer;
            this.issuedClaimSets = new ClaimSet[] { issuedClaims };
            this.id = Guid.NewGuid().ToString();
        }

        public ClaimSet Issuer { get { return this.issuer; } }

        public string Id { get { return this.id; } }

        public bool Evaluate(EvaluationContext context, ref object state)
        {
            foreach (ClaimSet issuance in this.issuedClaimSets)
            {
                context.AddClaimSet(this, issuance);
            }

            return true;
        }
    }
```

## <a name="displaying-the-callers-information"></a>Zobrazení informací o volajícím
 Chcete-li zobrazit informace o volajícím, `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` použijte, jak je znázorněno v následujícím ukázkovém kódu. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Obsahuje autorizační deklarace přidružené k aktuálnímu volajícímu. Deklarace identity jsou dodány `CreditCardToken` třídou ve své `AuthorizationPolicies` kolekci.

```csharp
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)
{
    claimValue = null;
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
        return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    enumerator.MoveNext();
    claimValue = (enumerator.Current.Resource == null) ? null :
        enumerator.Current.Resource.ToString();
    return true;
}

string GetCallerCreditCardNumber()
{
     foreach (ClaimSet claimSet in
         ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)
     {
         string creditCardNumber = null;
         if (TryGetStringClaimValue(claimSet,
             Constants.CreditCardNumberClaim, out creditCardNumber))
             {
                 string issuer;
                 if (!TryGetStringClaimValue(claimSet.Issuer,
                        ClaimTypes.Name, out issuer))
                 {
                     issuer = "Unknown";
                 }
                 return $"Credit card '{creditCardNumber}' issued by '{issuer}'";
        }
    }
    return "Credit card is not known";
}
```

 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

## <a name="setup-batch-file"></a>Nastavení dávkového souboru
 Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s příslušnými certifikáty pro spuštění aplikace hostované službou IIS, která vyžaduje zabezpečení založené na certifikátech serveru. Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.

 Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.

- Vytváří se certifikát serveru:

     Následující řádky ze `Setup.bat` souboru Batch vytvoří certifikát serveru, který se má použít. `%SERVER_NAME%` Proměnná Určuje název serveru. Změňte tuto proměnnou tak, aby určovala vlastní název serveru. Výchozí hodnota v tomto dávkovém souboru je localhost. Změníte-li `%SERVER_NAME%` proměnnou, je nutné projít soubory Client.cs a Service.cs a nahradit všechny instance místního hostitele názvem serveru, který používáte ve skriptu Setup. bat.

     Certifikát je uložený v osobním úložišti (osobní) v `LocalMachine` umístění úložiště. Certifikát je uložený v úložišti LocalMachine pro služby hostované službou IIS. Pro samoobslužné služby byste měli soubor Batch upravit tak, aby ukládal certifikát klienta do umístění úložiště CurrentUser, a to tak, že nahradíte řetězec LocalMachine řetězcem CurrentUser.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta:

     Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.

    ```
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Aby bylo možné povolit přístup k privátnímu klíči certifikátu ze služby hostované službou IIS, musí mít uživatelský účet, pod kterým je spuštěný proces hostovaný službou IIS, udělena příslušná oprávnění pro privátní klíč. To se provádí v posledních krocích skriptu Setup. bat.

    ```
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012. Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.

#### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači

1. Otevřete okno příkazového řádku sady Visual Studio 2012 s oprávněními správce a spusťte Setup. bat z ukázkové instalační složky. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky. Ujistěte se, že cesta obsahuje složku, ve které se nachází nástroj Makecert. exe.

> [!NOTE]
> Nezapomeňte odebrat certifikáty spuštěním souboru Cleanup. bat po dokončení ukázky. Další ukázky zabezpečení používají stejné certifikáty.  
  
1. Spusťte soubor Client. exe z adresáře client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
2. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computer"></a>Spuštění ukázky v rámci počítače  
  
1. Vytvořte adresář v počítači služby pro binární soubory služby.  
  
2. Zkopírujte programové soubory služby do adresáře služby na počítači služby. Nezapomeňte zkopírovat CreditCardFile. txt; jinak ověřovatel platební karty nemůže ověřit informace o kreditních kartách odeslaných z klienta. Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.  
  
3. Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Můžete ho vytvořit pomocí Setup. bat, pokud změníte `%SERVER_NAME%` proměnnou na plně kvalifikovaný název počítače, na kterém je služba hostovaná. Všimněte si, že soubor Setup. bat musí být spuštěný ve Developer Command Prompt pro Visual Studio, který se otevřel s oprávněními správce.  
  
4. Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople na klientovi. To je nutné provést pouze v případě, že certifikát serveru není vydán důvěryhodným vystavitelem.  
  
5. V souboru EchoServiceHost.cs změňte hodnotu názvu subjektu certifikátu a místo localhost zadejte plně kvalifikovaný název počítače.  
  
6. Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.  
  
7. V souboru Client.cs změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.  
  
8. V souboru Client.cs změňte název subjektu certifikátu X. 509 tak, aby odpovídal plně kvalifikovanému názvu počítače vzdáleného hostitele namísto localhost.  
  
9. V klientském počítači spusťte soubor Client. exe z okna příkazového řádku.  
  
10. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
1. Po dokončení ukázky spusťte na složce Samples Cleanup. bat.  
