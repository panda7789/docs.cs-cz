---
title: "Vlastní token"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19593e61cc640068ac7c90a6abbd6ea0d6a3ff08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-token"></a><span data-ttu-id="4677c-102">Vlastní token</span><span class="sxs-lookup"><span data-stu-id="4677c-102">Custom Token</span></span>
<span data-ttu-id="4677c-103">Tento příklad ukazuje, jak přidat vlastní tokenu implementaci do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="4677c-103">This sample demonstrates how to add a custom token implementation into a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="4677c-104">V příkladu se používá `CreditCardToken` bezpečně předávat informace o platebních kartách klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="4677c-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="4677c-105">Token je předán v záhlaví zprávy WS-zabezpečení a je podepsat a zašifrovat, pomocí vazby symetrický zabezpečení element společně s tělo zprávy a jiné záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="4677c-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="4677c-106">To je užitečné v případech, kdy jsou předdefinované tokeny není dostatečná.</span><span class="sxs-lookup"><span data-stu-id="4677c-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="4677c-107">Tento příklad znázorňuje, jak poskytnout token zabezpečení vlastní službě místo pomocí jedné z předdefinovaných tokenů.</span><span class="sxs-lookup"><span data-stu-id="4677c-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="4677c-108">Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4677c-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4677c-109">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4677c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4677c-110">Tento příklad znázorňuje to Shrneme, následující:</span><span class="sxs-lookup"><span data-stu-id="4677c-110">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="4677c-111">Jak klient předat token zabezpečení vlastní službu.</span><span class="sxs-lookup"><span data-stu-id="4677c-111">How a client can pass a custom security token to a service.</span></span>  
  
-   <span data-ttu-id="4677c-112">Jak služba může přijmout a ověřit token vlastní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4677c-112">How the service can consume and validate a custom security token.</span></span>  
  
-   <span data-ttu-id="4677c-113">Jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kódu služby můžete získat informace o tokeny přijaté zabezpečení včetně token vlastní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4677c-113">How the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service code can obtain the information about received security tokens including the custom security token.</span></span>  
  
-   <span data-ttu-id="4677c-114">Jak certifikát X.509 serveru slouží k ochraně symetrický klíč použitý k podpisu a šifrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="4677c-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>  
  
## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="4677c-115">Ověření klienta pomocí tokenu vlastní zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4677c-115">Client Authentication Using a Custom Security Token</span></span>  
 <span data-ttu-id="4677c-116">Službu zpřístupní jeden koncový bod, který je prostřednictvím kódu programu vytvořený pomocí `BindingHelper` a `EchoServiceHost` třídy.</span><span class="sxs-lookup"><span data-stu-id="4677c-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="4677c-117">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4677c-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="4677c-118">Vazba je nakonfigurována pomocí vlastních vazeb `SymmetricSecurityBindingElement` a `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="4677c-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="4677c-119">Nastaví Tato ukázka `SymmetricSecurityBindingElement` pro použití certifikátu X.509 služby chránit symetrický klíč během přenosu a předávat vlastní `CreditCardToken` v záhlaví zprávy WS-zabezpečení jako token zabezpečení podepsaná a šifrovaná.</span><span class="sxs-lookup"><span data-stu-id="4677c-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="4677c-120">Určuje chování služby přihlašovací údaje, které mají být použita pro ověřování klientů a také informace o certifikátu X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="4677c-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>  
  
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
  
 <span data-ttu-id="4677c-121">Využívat platební karty tokenu ve zprávě, ukázka používá vlastní služba pověření ke tuto funkčnost zajistit.</span><span class="sxs-lookup"><span data-stu-id="4677c-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="4677c-122">Třída přihlašovací údaje služby se nachází v `CreditCardServiceCredentials` třídy a přidají se do kolekce chování hostitele služby v `EchoServiceHost.InitializeRuntime` metoda.</span><span class="sxs-lookup"><span data-stu-id="4677c-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>  
  
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
  
 <span data-ttu-id="4677c-123">Koncový bod klienta je nakonfigurovaná podobným způsobem jako koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="4677c-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="4677c-124">Klient používá stejnou `BindingHelper` třída pro vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="4677c-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="4677c-125">Zbývající část nastavení se nachází v `Client` třídy.</span><span class="sxs-lookup"><span data-stu-id="4677c-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="4677c-126">Klient také nastaví informace, které mají být obsažena v `CreditCardToken` a informace o certifikátu X.509 služby v instalační kód přidáním `CreditCardClientCredentials` instance s správná data do kolekce chování klienta koncový bod.</span><span class="sxs-lookup"><span data-stu-id="4677c-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="4677c-127">Ukázka používá certifikát X.509 s názvem subjektu nastavit na `CN=localhost` jako certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="4677c-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>  
  
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
  
## <a name="custom-security-token-implementation"></a><span data-ttu-id="4677c-128">Token implementace vlastního zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4677c-128">Custom Security Token Implementation</span></span>  
 <span data-ttu-id="4677c-129">Chcete-li povolit token vlastní zabezpečení v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vytvořit reprezentaci objektu tokenu vlastní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4677c-129">To enable a custom security token in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], create an object representation of the custom security token.</span></span> <span data-ttu-id="4677c-130">Ukázka má tento reprezentace v `CreditCardToken` třídy.</span><span class="sxs-lookup"><span data-stu-id="4677c-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="4677c-131">Reprezentace objektu je zodpovědný za podržíte všechny relevantní informace o tokenu zabezpečení a které poskytují seznam klíčů zabezpečení obsažených v tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4677c-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="4677c-132">V takovém případě platební karty token zabezpečení neobsahuje žádné klíč zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4677c-132">In this case, the credit card security token does not contain any security key.</span></span>  
  
 <span data-ttu-id="4677c-133">Další část popisuje, co musíte udělat povolit vlastní token má být přenesen prostřednictvím sítě a spotřebovávají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod.</span><span class="sxs-lookup"><span data-stu-id="4677c-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint.</span></span>  
  
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
  
## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="4677c-134">Získání tokenu do a ze zprávy vlastní platební karty</span><span class="sxs-lookup"><span data-stu-id="4677c-134">Getting the Custom Credit Card Token to and from the Message</span></span>  
 <span data-ttu-id="4677c-135">Serializátorů tokenu zabezpečení v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou zodpovědní za vytváření reprezentaci objektu tokenů zabezpečení z XML ve zprávě a vytvoření formuláře XML tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4677c-135">Security token serializers in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="4677c-136">Rovněž jsou zodpovědní za další funkce, jako je například čtení a zápis klíče identifikátory odkazující na tokeny zabezpečení, ale tento příklad používá jenom zabezpečení související s tokeny funkce.</span><span class="sxs-lookup"><span data-stu-id="4677c-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="4677c-137">Chcete-li povolit vlastní tokenu je nutné implementovat vlastní serializátoru tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4677c-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="4677c-138">V tomto příkladu `CreditCardSecurityTokenSerializer` třídu pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="4677c-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>  
  
 <span data-ttu-id="4677c-139">Ve službě vlastní serializátor přečte formulář XML vlastní tokenu a slouží k vyjádření objektu vlastní tokenu z něj.</span><span class="sxs-lookup"><span data-stu-id="4677c-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>  
  
 <span data-ttu-id="4677c-140">Na straně klienta `CreditCardSecurityTokenSerializer` třída zapíše informace obsažené v rámci reprezentace objektu tokenu zabezpečení do zapisovače XML.</span><span class="sxs-lookup"><span data-stu-id="4677c-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>  
  
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
  
## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="4677c-141">Vytváření zprostředkovatele tokenu a Token ověřovací třídy</span><span class="sxs-lookup"><span data-stu-id="4677c-141">How Token Provider and Token Authenticator Classes are Created</span></span>  
 <span data-ttu-id="4677c-142">Přihlašovací údaje klient a služba je zodpovědná za poskytování instance Správce tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4677c-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="4677c-143">Instance Správce tokenu zabezpečení se používá k získání poskytovatele tokenů, ověřovací data tokenu a serializátorů tokenu.</span><span class="sxs-lookup"><span data-stu-id="4677c-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>  
  
 <span data-ttu-id="4677c-144">Zprostředkovatel tokenu vytvoří reprezentaci objektu tokenu na základě informací obsažených v klienta služby Windows nebo pověření.</span><span class="sxs-lookup"><span data-stu-id="4677c-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="4677c-145">Reprezentace objektu tokenu se pak zapíše zprávu pomocí serializátoru tokenů (popsané v předchozí části).</span><span class="sxs-lookup"><span data-stu-id="4677c-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>  
  
 <span data-ttu-id="4677c-146">Ověřovací data tokenu ověřuje tokeny, které přicházejí ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="4677c-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="4677c-147">Příchozí reprezentace objektu tokenu je vytvořený serializátoru tokenů.</span><span class="sxs-lookup"><span data-stu-id="4677c-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="4677c-148">Tento objekt reprezentace se pak předá do ověřovacího modulu tokenu pro ověření.</span><span class="sxs-lookup"><span data-stu-id="4677c-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="4677c-149">Po úspěšném ověření tokenu ověřovací data tokenu vrátí kolekci `IAuthorizationPolicy` objekty, které představují informací obsažených v tokenu.</span><span class="sxs-lookup"><span data-stu-id="4677c-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="4677c-150">Tyto informace slouží později v průběhu zpracování zpráv k provedení rozhodnutí o autorizaci a poskytovat deklarace identity pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4677c-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="4677c-151">V tomto příkladu se používá ověřovací data tokenu platební karty `CreditCardTokenAuthorizationPolicy` pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="4677c-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>  
  
 <span data-ttu-id="4677c-152">Serializátoru tokenů zodpovídá za načítání reprezentace objektu tokenu do a ze sítě.</span><span class="sxs-lookup"><span data-stu-id="4677c-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="4677c-153">Je to popsané v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="4677c-153">This is discussed in the previous section.</span></span>  
  
 <span data-ttu-id="4677c-154">V této ukázce používáme zprostředkovatele tokenu jenom na klientovi a ověřovací data tokenu pouze na služby, protože chceme přenášet token platební karty pouze ve směru klient služba.</span><span class="sxs-lookup"><span data-stu-id="4677c-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>  
  
 <span data-ttu-id="4677c-155">Funkce na klientovi se nachází v `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` a `CreditCardTokenProvider` třídy.</span><span class="sxs-lookup"><span data-stu-id="4677c-155">The functionality on the client is located in the `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>  
  
 <span data-ttu-id="4677c-156">Funkce na službu, který se nachází v `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` a `CreditCardTokenAuthorizationPolicy` třídy.</span><span class="sxs-lookup"><span data-stu-id="4677c-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>  
  
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
  
## <a name="displaying-the-callers-information"></a><span data-ttu-id="4677c-157">Zobrazení informací o volající.</span><span class="sxs-lookup"><span data-stu-id="4677c-157">Displaying the Callers' Information</span></span>  
 <span data-ttu-id="4677c-158">Chcete-li zobrazit informace volajícího, použijte `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4677c-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="4677c-159">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Obsahuje spojené s volajícím aktuální deklarací autorizace.</span><span class="sxs-lookup"><span data-stu-id="4677c-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="4677c-160">Deklarace identity, které jsou poskytovány společností `CreditCardToken` třídy v jeho `AuthorizationPolicies` kolekce.</span><span class="sxs-lookup"><span data-stu-id="4677c-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>  
  
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
  
 <span data-ttu-id="4677c-161">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="4677c-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4677c-162">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="4677c-162">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="4677c-163">Instalační program dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="4677c-163">Setup Batch File</span></span>  
 <span data-ttu-id="4677c-164">Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění aplikace hostované službou IIS, která vyžaduje zabezpečení na základě certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="4677c-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="4677c-165">Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.</span><span class="sxs-lookup"><span data-stu-id="4677c-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="4677c-166">Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4677c-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="4677c-167">Vytvoření certifikátu serveru:</span><span class="sxs-lookup"><span data-stu-id="4677c-167">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="4677c-168">Následující řádků z `Setup.bat` dávkový soubor vytvořte certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="4677c-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="4677c-169">`%SERVER_NAME%` Proměnná Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="4677c-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="4677c-170">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="4677c-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="4677c-171">V tento dávkový soubor výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="4677c-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="4677c-172">Pokud změníte `%SERVER_NAME%` proměnné, musíte projít Client.cs a Service.cs soubory a název serveru, který používáte ve skriptu Setup.bat nahraďte všechny výskyty localhost.</span><span class="sxs-lookup"><span data-stu-id="4677c-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>  
  
     <span data-ttu-id="4677c-173">Certifikát je uložen v tomto úložišti (osobních) v části `LocalMachine` umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="4677c-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="4677c-174">Certifikát je uložen v úložišti LocalMachine pro služby hostované službou IIS.</span><span class="sxs-lookup"><span data-stu-id="4677c-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="4677c-175">Pro samoobslužné hostované služby upravte dávkový soubor pro uložení certifikátu klienta v umístění úložiště CurrentUser nahrazením řetězec LocalMachine CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="4677c-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="4677c-176">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="4677c-176">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="4677c-177">Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště.</span><span class="sxs-lookup"><span data-stu-id="4677c-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="4677c-178">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="4677c-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="4677c-179">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="4677c-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    echo ************  
    echo copying server cert to client's TrustedPeople store  
    echo ************  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="4677c-180">Povolit přístup k privátnímu klíči certifikátu ze služby hostované službou IIS, musí mít uživatelský účet, pod kterým je spuštěn proces hostované službou IIS udělen příslušná oprávnění pro privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="4677c-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="4677c-181">To lze provést poslední kroky ve skriptu Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="4677c-181">This is accomplished by last steps in the Setup.bat script.</span></span>  
  
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
>  <span data-ttu-id="4677c-182">Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4677c-182">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="4677c-183">Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="4677c-183">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="4677c-184">Jak nastavit a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="4677c-184">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="4677c-185">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4677c-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4677c-186">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4677c-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="4677c-187">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="4677c-187">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="4677c-188">Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] okno příkazového řádku s oprávněními správce a spusťte Setup.bat ve složce instalace ukázkové.</span><span class="sxs-lookup"><span data-stu-id="4677c-188">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="4677c-189">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky. Ujistěte se, že cesta obsahuje složku, kde je umístěna Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="4677c-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4677c-190">Je nutné certifikáty odebrat spuštěním Cleanup.bat po dokončení se vzorkem.</span><span class="sxs-lookup"><span data-stu-id="4677c-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="4677c-191">Další ukázky zabezpečení použijte stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="4677c-191">Other security samples use the same certificates.</span></span>  
  
1.  <span data-ttu-id="4677c-192">Spusťte Client.exe z adresáře client\bin.</span><span class="sxs-lookup"><span data-stu-id="4677c-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="4677c-193">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="4677c-193">Client activity is displayed on the client console application.</span></span>  
  
2.  <span data-ttu-id="4677c-194">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="4677c-194">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="4677c-195">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="4677c-195">To run the sample across computer</span></span>  
  
1.  <span data-ttu-id="4677c-196">Vytvořte adresář na počítači se službou pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="4677c-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="4677c-197">Zkopírujte soubory programu služby do adresáře služby na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="4677c-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="4677c-198">Nezapomeňte zkopírovat CreditCardFile.txt; v opačném případě authenticator platební karty nelze ověřit informace o kreditní kartě odeslaných z klienta.</span><span class="sxs-lookup"><span data-stu-id="4677c-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="4677c-199">Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="4677c-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="4677c-200">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="4677c-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="4677c-201">Můžete vytvořit pomocí Setup.bat, pokud změníte `%SERVER_NAME%` proměnnou plně kvalifikovaný název počítače, který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="4677c-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="4677c-202">Všimněte si, že soubor Setup.bat je nutné spustit z příkazového řádku Visual Studia otevřít s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4677c-202">Note that the Setup.bat file must be run in a Visual Studio command prompt opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="4677c-203">Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople v klientovi.</span><span class="sxs-lookup"><span data-stu-id="4677c-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="4677c-204">Musí provést pouze v případě, že certifikát serveru není vystavený důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="4677c-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="4677c-205">V souboru EchoServiceHost.cs změňte hodnotu názvu subjektu certifikátu k zadání názvu počítače plně kvalifikovaný místo localhost.</span><span class="sxs-lookup"><span data-stu-id="4677c-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="4677c-206">Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.</span><span class="sxs-lookup"><span data-stu-id="4677c-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7.  <span data-ttu-id="4677c-207">V souboru Client.cs změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="4677c-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8.  <span data-ttu-id="4677c-208">V souboru Client.cs změňte název předmětu certifikátu X.509 služby tak, aby odpovídala plně kvalifikovaný název hostitele vzdálené místo localhost.</span><span class="sxs-lookup"><span data-stu-id="4677c-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="4677c-209">Na klientském počítači spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4677c-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="4677c-210">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="4677c-210">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="4677c-211">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="4677c-211">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="4677c-212">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="4677c-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4677c-213">Viz také</span><span class="sxs-lookup"><span data-stu-id="4677c-213">See Also</span></span>
