---
title: Vlastní token
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: c7219b94861cd23f27b331d1d3e5509654263430
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="custom-token"></a>Vlastní token
Tento příklad ukazuje, jak přidat vlastní implementaci token do aplikace Windows Communication Foundation (WCF). V příkladu se používá `CreditCardToken` bezpečně předávat informace o platebních kartách klienta ke službě. Token je předán v záhlaví zprávy WS-zabezpečení a je podepsat a zašifrovat, pomocí vazby symetrický zabezpečení element společně s tělo zprávy a jiné záhlaví zprávy. To je užitečné v případech, kdy jsou předdefinované tokeny není dostatečná. Tento příklad znázorňuje, jak poskytnout token zabezpečení vlastní službě místo pomocí jedné z předdefinovaných tokenů. Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tento příklad znázorňuje to Shrneme, následující:  
  
-   Jak klient předat token zabezpečení vlastní službu.  
  
-   Jak služba může přijmout a ověřit token vlastní zabezpečení.  
  
-   Jak kódu služby WCF můžete získat informace o tokeny přijaté zabezpečení včetně token vlastní zabezpečení.  
  
-   Jak certifikát X.509 serveru slouží k ochraně symetrický klíč použitý k podpisu a šifrování zpráv.  
  
## <a name="client-authentication-using-a-custom-security-token"></a>Ověření klienta pomocí tokenu vlastní zabezpečení  
 Službu zpřístupní jeden koncový bod, který je prostřednictvím kódu programu vytvořený pomocí `BindingHelper` a `EchoServiceHost` třídy. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována pomocí vlastních vazeb `SymmetricSecurityBindingElement` a `HttpTransportBindingElement`. Nastaví Tato ukázka `SymmetricSecurityBindingElement` pro použití certifikátu X.509 služby chránit symetrický klíč během přenosu a předávat vlastní `CreditCardToken` v záhlaví zprávy WS-zabezpečení jako token zabezpečení podepsaná a šifrovaná. Určuje chování služby přihlašovací údaje, které mají být použita pro ověřování klientů a také informace o certifikátu X.509 služby.  
  
```  
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
  
 Využívat platební karty tokenu ve zprávě, ukázka používá vlastní služba pověření ke tuto funkčnost zajistit. Třída přihlašovací údaje služby se nachází v `CreditCardServiceCredentials` třídy a přidají se do kolekce chování hostitele služby v `EchoServiceHost.InitializeRuntime` metoda.  
  
```  
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
  
 Koncový bod klienta je nakonfigurovaná podobným způsobem jako koncový bod služby. Klient používá stejnou `BindingHelper` třída pro vytvoření vazby. Zbývající část nastavení se nachází v `Client` třídy. Klient také nastaví informace, které mají být obsažena v `CreditCardToken` a informace o certifikátu X.509 služby v instalační kód přidáním `CreditCardClientCredentials` instance s správná data do kolekce chování klienta koncový bod. Ukázka používá certifikát X.509 s názvem subjektu nastavit na `CN=localhost` jako certifikát služby.  
  
```  
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();  
EndpointAddress serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
  
// Create a client with given client endpoint configuration  
channelFactory =   
new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);  
  
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
  
## <a name="custom-security-token-implementation"></a>Token implementace vlastního zabezpečení  
 Pokud chcete povolit token vlastní zabezpečení ve WCF, vytvořte reprezentaci objektu tokenu vlastní zabezpečení. Ukázka má tento reprezentace v `CreditCardToken` třídy. Reprezentace objektu je zodpovědný za podržíte všechny relevantní informace o tokenu zabezpečení a které poskytují seznam klíčů zabezpečení obsažených v tokenu zabezpečení. V takovém případě platební karty token zabezpečení neobsahuje žádné klíč zabezpečení.  
  
 Další část popisuje, co musíte udělat povolit vlastní token má být přenesen prostřednictvím sítě a spotřebovávají koncový bod WCF.  
  
```  
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
  
## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>Získání tokenu do a ze zprávy vlastní platební karty  
 Serializátorů tokenů zabezpečení ve WCF jsou zodpovědní za vytváření reprezentaci objektu tokenů zabezpečení z XML ve zprávě a vytvoření formuláře XML tokenů zabezpečení. Rovněž jsou zodpovědní za další funkce, jako je například čtení a zápis klíče identifikátory odkazující na tokeny zabezpečení, ale tento příklad používá jenom zabezpečení související s tokeny funkce. Chcete-li povolit vlastní tokenu je nutné implementovat vlastní serializátoru tokenů zabezpečení. V tomto příkladu `CreditCardSecurityTokenSerializer` třídu pro tento účel.  
  
 Ve službě vlastní serializátor přečte formulář XML vlastní tokenu a slouží k vyjádření objektu vlastní tokenu z něj.  
  
 Na straně klienta `CreditCardSecurityTokenSerializer` třída zapíše informace obsažené v rámci reprezentace objektu tokenu zabezpečení do zapisovače XML.  
  
```  
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
  
## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>Vytváření zprostředkovatele tokenu a Token ověřovací třídy  
 Přihlašovací údaje klient a služba je zodpovědná za poskytování instance Správce tokenu zabezpečení. Instance Správce tokenu zabezpečení se používá k získání poskytovatele tokenů, ověřovací data tokenu a serializátorů tokenu.  
  
 Zprostředkovatel tokenu vytvoří reprezentaci objektu tokenu na základě informací obsažených v klienta služby Windows nebo pověření. Reprezentace objektu tokenu se pak zapíše zprávu pomocí serializátoru tokenů (popsané v předchozí části).  
  
 Ověřovací data tokenu ověřuje tokeny, které přicházejí ve zprávě. Příchozí reprezentace objektu tokenu je vytvořený serializátoru tokenů. Tento objekt reprezentace se pak předá do ověřovacího modulu tokenu pro ověření. Po úspěšném ověření tokenu ověřovací data tokenu vrátí kolekci `IAuthorizationPolicy` objekty, které představují informací obsažených v tokenu. Tyto informace slouží později v průběhu zpracování zpráv k provedení rozhodnutí o autorizaci a poskytovat deklarace identity pro aplikaci. V tomto příkladu se používá ověřovací data tokenu platební karty `CreditCardTokenAuthorizationPolicy` pro tento účel.  
  
 Serializátoru tokenů zodpovídá za načítání reprezentace objektu tokenu do a ze sítě. Je to popsané v předchozí části.  
  
 V této ukázce používáme zprostředkovatele tokenu jenom na klientovi a ověřovací data tokenu pouze na služby, protože chceme přenášet token platební karty pouze ve směru klient služba.  
  
 Funkce na klientovi se nachází v `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` a `CreditCardTokenProvider` třídy.  
  
 Funkce na službu, který se nachází v `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` a `CreditCardTokenAuthorizationPolicy` třídy.  
  
```  
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
  
## <a name="displaying-the-callers-information"></a>Zobrazení informací o volající.  
 Chcete-li zobrazit informace volajícího, použijte `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak je znázorněno v následujícím ukázkovém kódu. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Obsahuje spojené s volajícím aktuální deklarací autorizace. Deklarace identity, které jsou poskytovány společností `CreditCardToken` třídy v jeho `AuthorizationPolicies` kolekce.  
  
```  
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)  
{  
    claimValue = null;  
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType,  
        Rights.PossessProperty);  
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
                 return String.Format(  
                   "Credit card '{0}' issued by '{1}'",   
                   creditCardNumber, issuer);  
        }  
    }  
    return "Credit card is not known";  
}  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
## <a name="setup-batch-file"></a>Instalační program dávkového souboru  
 Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění aplikace hostované službou IIS, která vyžaduje zabezpečení na základě certifikátu serveru. Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci.  
  
-   Vytvoření certifikátu serveru:  
  
     Následující řádků z `Setup.bat` dávkový soubor vytvořte certifikát serveru, který chcete použít. `%SERVER_NAME%` Proměnná Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. V tento dávkový soubor výchozí hodnota je localhost. Pokud změníte `%SERVER_NAME%` proměnné, musíte projít Client.cs a Service.cs soubory a název serveru, který používáte ve skriptu Setup.bat nahraďte všechny výskyty localhost.  
  
     Certifikát je uložen v tomto úložišti (osobních) v části `LocalMachine` umístění úložiště. Certifikát je uložen v úložišti LocalMachine pro služby hostované službou IIS. Pro samoobslužné hostované služby upravte dávkový soubor pro uložení certifikátu klienta v umístění úložiště CurrentUser nahrazením řetězec LocalMachine CurrentUser.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:  
  
     Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    echo ************  
    echo copying server cert to client's TrustedPeople store  
    echo ************  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Povolit přístup k privátnímu klíči certifikátu ze služby hostované službou IIS, musí mít uživatelský účet, pod kterým je spuštěn proces hostované službou IIS udělen příslušná oprávnění pro privátní klíč. To lze provést poslední kroky ve skriptu Setup.bat.  
  
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
>  Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Jak nastavit a sestavit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] okno příkazového řádku s oprávněními správce a spusťte Setup.bat ve složce instalace ukázkové. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky. Ujistěte se, že cesta obsahuje složku, kde je umístěna Makecert.exe.  
  
> [!NOTE]
>  Je nutné certifikáty odebrat spuštěním Cleanup.bat po dokončení se vzorkem. Další ukázky zabezpečení použijte stejné certifikáty.  
  
1.  Spusťte Client.exe z adresáře client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
2.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computer"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvořte adresář na počítači se službou pro binární soubory služby.  
  
2.  Zkopírujte soubory programu služby do adresáře služby na počítači se službou. Nezapomeňte zkopírovat CreditCardFile.txt; v opačném případě authenticator platební karty nelze ověřit informace o kreditní kartě odeslaných z klienta. Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3.  Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Můžete vytvořit pomocí Setup.bat, pokud změníte `%SERVER_NAME%` proměnnou plně kvalifikovaný název počítače, který je hostitelem služby. Všimněte si, že soubor Setup.bat je nutné spustit z příkazového řádku Visual Studia otevřít s oprávněními správce.  
  
4.  Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople v klientovi. Musí provést pouze v případě, že certifikát serveru není vystavený důvěryhodných vystavitelů.  
  
5.  V souboru EchoServiceHost.cs změňte hodnotu názvu subjektu certifikátu k zadání názvu počítače plně kvalifikovaný místo localhost.  
  
6.  Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.  
  
7.  V souboru Client.cs změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.  
  
8.  V souboru Client.cs změňte název předmětu certifikátu X.509 služby tak, aby odpovídala plně kvalifikovaný název hostitele vzdálené místo localhost.  
  
9. Na klientském počítači spusťte Client.exe z okna příkazového řádku.  
  
10. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
1.  Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
## <a name="see-also"></a>Viz také
