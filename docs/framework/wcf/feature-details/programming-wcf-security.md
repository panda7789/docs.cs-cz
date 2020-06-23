---
title: Programování zabezpečení WCF
description: Naučte se vytvořit zabezpečenou aplikaci WCF, včetně ověřování, důvěrnosti a integrity.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 8e77c667dd8904c10bbab88e1413690677cef53b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244982"
---
# <a name="programming-wcf-security"></a>Programování zabezpečení WCF
Toto téma popisuje základní programovací úkoly, které slouží k vytvoření zabezpečené aplikace Windows Communication Foundation (WCF). Toto téma se věnuje pouze ověřování, důvěrnosti a integritě, které se souhrnně označují jako *zabezpečení přenosu*. Toto téma nezahrnuje autorizaci (kontrolu přístupu k prostředkům a službám); informace o autorizaci najdete v tématu [autorizace](authorization-in-wcf.md).  
  
> [!NOTE]
> Důležité informace o konceptech zabezpečení, zejména v souvislosti s WCF, najdete v tématu kurzy k sadě vzorů a postupů na webu MSDN ve [scénářích, vzorcích a návodech k implementaci pro vylepšení webových služeb (WSE) 3,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10)).  
  
 Programování zabezpečení WCF je založené na třech krocích nastavení následujících: režim zabezpečení, typ pověření klienta a hodnoty přihlašovacích údajů. Tyto kroky můžete provést buď prostřednictvím kódu, nebo pomocí konfigurace.  
  
## <a name="setting-the-security-mode"></a>Nastavení režimu zabezpečení  
 V následující části najdete obecné kroky pro programování v rámci služby WCF v režimu zabezpečení:  
  
1. Vyberte jednu z předdefinovaných vazeb odpovídající vašim požadavkům vaší aplikace. Seznam možností vazby najdete v tématu [vazby poskytované systémem](../system-provided-bindings.md). Ve výchozím nastavení má skoro každá vazba povolenou možnost zabezpečení. Jedinou výjimkou je <xref:System.ServiceModel.BasicHttpBinding> třída (pomocí konfigurace, a [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ).  
  
     Vybraná vazba určuje přenos. Například <xref:System.ServiceModel.WSHttpBinding> jako přenos používá protokol HTTP; <xref:System.ServiceModel.NetTcpBinding> používá protokol TCP.  
  
2. Vyberte jeden z režimů zabezpečení pro vazbu. Všimněte si, že vybraná vazba Určuje dostupné možnosti režimu. Například <xref:System.ServiceModel.WSDualHttpBinding> nepovoluje zabezpečení přenosu (není to možnost). Podobně není <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> <xref:System.ServiceModel.NetNamedPipeBinding> povolena ani zabezpečení zpráv.  
  
     Máte tři možnosti:  
  
    1. `Transport`  
  
         Zabezpečení přenosu závisí na mechanismu, který vybraná vazba používá. Pokud například používáte, `WSHttpBinding` je mechanismus zabezpečení SSL (Secure Sockets Layer) (SSL) (také mechanismus protokolu HTTPS). Obecně řečeno, hlavní výhodou zabezpečení přenosu spočívá v tom, že zajišťuje dobrou propustnost bez ohledu na to, jaký přenos používáte. Má ale dvě omezení: první je, že transportní mechanismus využije typ přihlašovacích údajů, který se používá k ověření uživatele. Toto je nevýhoda pouze v případě, že služba potřebuje spolupracovat s jinými službami, které požadují různé typy přihlašovacích údajů. Je to proto, že vzhledem k tomu, že se zabezpečení na úrovni zprávy nepoužívá, je zabezpečení implementováno v rámci směrování po směrování a nikoli od začátku do konce. Toto omezení je problémem jenom v případě, že cesta ke zprávě mezi klientem a službou zahrnuje prostředníky. Další informace o tom, jaký přenos se má použít, najdete v tématu [Volba přenosu](choosing-a-transport.md). Další informace o použití zabezpečení přenosu najdete v tématu [Přehled zabezpečení přenosu](transport-security-overview.md).  
  
    2. `Message`  
  
         Zabezpečení zpráv znamená, že každá zpráva obsahuje potřebné hlavičky a data, aby byla zpráva zabezpečená. Vzhledem k tomu, že se složení hlaviček liší, můžete zahrnout libovolný počet přihlašovacích údajů. To se může jednat o faktor, Pokud spolupracujete s jinými službami, které požadují konkrétní typ přihlašovacích údajů, který transportní mechanismus nemůže dodat, nebo pokud se zpráva musí použít s více než jednou službou, kde každá služba vyžaduje jiný typ přihlašovacích údajů.  
  
         Další informace najdete v tématu [zabezpečení zpráv](message-security-in-wcf.md).  
  
    3. `TransportWithMessageCredential`  
  
         Tato volba používá přenosovou vrstvu k zabezpečení přenosu zpráv, zatímco každá zpráva obsahuje bohatě zajištěné přihlašovací údaje, které vyžadují jiné služby. To kombinuje výkon zabezpečení přenosu s využitím bohatých přihlašovacích údajů pro zabezpečení zpráv. K dispozici jsou následující vazby: <xref:System.ServiceModel.BasicHttpBinding> , <xref:System.ServiceModel.WSFederationHttpBinding> , <xref:System.ServiceModel.NetPeerTcpBinding> a <xref:System.ServiceModel.WSHttpBinding> .  
  
3. Pokud se rozhodnete použít zabezpečení přenosu pro protokol HTTP (jinými slovy, HTTPS), musíte také nakonfigurovat hostitele s certifikátem SSL a povolit SSL na portu. Další informace najdete v tématu [zabezpečení přenosu HTTP](http-transport-security.md).  
  
4. Pokud používáte <xref:System.ServiceModel.WSHttpBinding> a nepotřebujete vytvořit zabezpečenou relaci, nastavte <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost na hodnotu `false` .  
  
     Zabezpečená relace nastane, když klient a služba vytvoří kanál pomocí symetrického klíče (klient a server používají stejný klíč pro délku konverzace, dokud se dialog nezavře).  
  
## <a name="setting-the-client-credential-type"></a>Nastavení typu pověření klienta  
 Podle potřeby vyberte typ přihlašovacích údajů klienta. Další informace najdete v tématu [Výběr typu přihlašovacích údajů](selecting-a-credential-type.md). K dispozici jsou následující typy přihlašovacích údajů klienta:  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 V závislosti na nastavení režimu musíte nastavit typ přihlašovacích údajů. Pokud jste například vybrali `wsHttpBinding` a nastavili režim na "zpráva", můžete také nastavit `clientCredentialType` atribut prvku zprávy na jednu z následujících hodnot: `None` , `Windows` , `UserName` , `Certificate` a `IssuedToken` , jak je znázorněno v následujícím příkladu konfigurace.  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 Nebo v kódu:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Nastavují se hodnoty přihlašovacích údajů služby.  
 Jakmile vyberete typ přihlašovacích údajů klienta, musíte nastavit vlastní přihlašovací údaje pro službu a klienta, které chcete použít. Ve službě jsou přihlašovací údaje nastaveny pomocí <xref:System.ServiceModel.Description.ServiceCredentials> třídy a vráceny <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastností <xref:System.ServiceModel.ServiceHostBase> třídy. Použitá vazba implikuje typ pověření služby, zvolený režim zabezpečení a typ přihlašovacích údajů klienta. Následující kód nastaví certifikát pro pověření služby.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Nastavování hodnot přihlašovacích údajů klienta  
 Na straně klienta nastavte hodnoty přihlašovacích údajů klienta pomocí <xref:System.ServiceModel.Description.ClientCredentials> třídy a vrácené <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastností <xref:System.ServiceModel.ClientBase%601> třídy. Následující kód nastaví certifikát jako přihlašovací údaje v klientovi pomocí protokolu TCP.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Základní programování WCF](../basic-wcf-programming.md)
- [Běžné scénáře zabezpečení](common-security-scenarios.md)
