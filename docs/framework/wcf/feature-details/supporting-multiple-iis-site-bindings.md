---
title: Podpora víc vazeb webu IIS
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 5a8b06d86b505452f9ded808f727343b1453e592
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840861"
---
# <a name="supporting-multiple-iis-site-bindings"></a>Podpora víc vazeb webu IIS
Při hostování služby Windows Communication Foundation (WCF) v části Internet Information Services (IIS) 7.0, můžete chtít poskytnout více základní adresy, které používají stejný protokol na stejném místě. To umožňuje stejnou službu reagovat na celou řadou různých identifikátorů URI. To je užitečné, pokud chcete hostovat službu, která naslouchá na `http://www.contoso.com` a `http://contoso.com`. Je také užitečné, pokud chcete vytvořit službu, která má bázové adresy pro interní uživatele a samostatné základní adresu pro externí uživatele. Příklad: `http://internal.contoso.com` a `http://www.contoso.com`.  
  
> [!NOTE]
>  Tato funkce je pouze k dispozici prostřednictvím protokolu HTTP.  
  
## <a name="multiple-base-addresses"></a>Vícenásobné základní adresy  
 Tato funkce dostupná pouze pro služby WCF hostované v rámci služby IIS. Tato funkce není povolena ve výchozím nastavení. K tomu je nutné přidat `multipleSiteBindingsEnabled` atribut <`serviceHostingEnvironment`> element v souboru Web.config souboru a nastavte ho na `true`, jak je znázorněno v následujícím příkladu.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 Při hostování služby WCF v IIS, služba IIS vytvoří jednu bázovou adresu založené na identifikátor URI pro virtuální adresář, který obsahuje aplikaci. Můžete přidat další základní adresy, které používají stejný protokol pomocí Správce Internetové informační služby přidat jednu nebo více vazeb webu. Pro každou vazbu zadejte protokol (HTTP nebo HTTPS), IP adresu, port a název hostitele. Další informace o používání Správce Internetové informační služby najdete v tématu [Správce služby IIS (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164057). Další informace o přidávání vazeb k lokalitě najdete v tématu [vytvoření webového serveru (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Určení více bázové adresy pro stejnou lokalitu má vliv na obsah stránka nápovědy WCF, import schématu a WSDL a MEX informace vygenerované službou. Na stránce nápovědy WCF zobrazí příkazový řádek pro generování klienta WCF, který může komunikovat se službou. Tento příkazový řádek obsahuje pouze první adresa zadaná ve vazbě služby IIS pro web. Podobně při importu schématu, pouze první základní adresa zadaná ve vazbě IIS používá. WSDL a MEX data obsahují všechny základní adresy určené v vazby služby IIS.  
  
> [!WARNING]
>  To znamená, že pokud služba má dvě základní adresy, jednu pro interní uživatele a druhou pro externí uživatele, jsou zadány oba v informacích o WSDL a MEX vygenerované službou.
