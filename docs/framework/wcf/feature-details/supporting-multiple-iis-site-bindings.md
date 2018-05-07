---
title: Podpora víc vazeb webu IIS
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 9b92243bb7aaea5c8ecf708ce863e6979bc9f17c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="supporting-multiple-iis-site-bindings"></a>Podpora víc vazeb webu IIS
Při hostování služby Windows Communication Foundation (WCF) v části Internetové informační služby (IIS) 7.0, můžete zadat více základní adresy, která používá stejný protokol ve stejné lokalitě. To umožňuje stejnou službu reagovat na několika různých identifikátory URI. To je užitečné, když chcete hostovat službu, která naslouchá na http://www.contoso.com a http://contoso.com. Je také užitečné k vytvoření služby, který má bázové adresy pro interní uživatele a samostatné základní adresa pro externí uživatele. Příklad: http://internal.contoso.com a http://www.contoso.com.  
  
> [!NOTE]
>  Tato funkce je dostupná, pomocí protokolu HTTP jenom.  
  
## <a name="multiple-base-addresses"></a>Vícenásobné základní adresy  
 Tato funkce je jenom ke službám WCF, které jsou hostované v rámci služby IIS k dispozici. Tato funkce není povolená ve výchozím nastavení. Povolit, je nutné přidat `multipleSiteBindingsEnabled` atribut <`serviceHostingEnvironment`> element v souboru Web.config souborů a nastavte ji na `true`, jak je znázorněno v následujícím příkladu.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 Při hostování služby WCF v IIS, služba IIS vytvoří jednu základní adresu založené na identifikátor URI virtuálního adresáře, který obsahuje aplikaci. Můžete přidat další základní adresy, které používají stejný protokol pomocí Správce Internetové informační služby přidat jeden nebo více vazby na webové stránky. Pro každou vazbu zadejte protokol (HTTP nebo HTTPS), adresu IP, portu a názvu hostitele. Další informace o používání Správce Internetové informační služby najdete v tématu [Správce služby IIS (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057). Další informace o přidávání vazeb k lokalitě najdete v tématu [vytvoření webového serveru (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Zadání více základní adresy pro stejnou lokalitu ovlivňuje obsahu stránce nápovědy k WCF, import schématu a informace WSDL/MEX vygenerované službou. Na stránce nápovědy WCF zobrazí příkazový řádek, který používá ke generování klienta WCF, který může komunikovat se službou. Tento příkaz obsahuje pouze první adresa zadaná v vazby služby IIS pro web. Podobně když import schématu, pouze první základní adresu určenou v IIS vazby se používá. WSDL a MEX data obsahovat všechny základní adresami uvedenými v vazby služby IIS.  
  
> [!WARNING]
>  To znamená, že pokud služba má dvě základní adresy, jednu pro interní uživatele a druhou pro externí uživatele, jsou zadány oba ve schématu WSDL/MEX informace vygenerované službou.
