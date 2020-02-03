---
title: Podpora víc vazeb webu IIS
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: e364be55687323d3059c4a7e084818e3f7d54d5f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743440"
---
# <a name="supporting-multiple-iis-site-bindings"></a>Podpora víc vazeb webu IIS
Při hostování služby Windows Communication Foundation (WCF) pod Internetová informační služba (IIS) 7,0 možná budete chtít poskytnout více základních adres, které používají stejný protokol na stejné lokalitě. To umožňuje stejné službě reagovat na několik různých identifikátorů URI. To je užitečné, když chcete hostovat službu, která naslouchá na `http://www.contoso.com` a `http://contoso.com`. Také je užitečné vytvořit službu, která má základní adresu pro interní uživatele a samostatnou základní adresu pro externí uživatele. Například: `http://internal.contoso.com` a `http://www.contoso.com`  
  
> [!NOTE]
> Tato funkce je k dispozici pouze pomocí protokolu HTTP.  
  
## <a name="multiple-base-addresses"></a>Několik základních adres  
 Tato funkce je dostupná pouze pro služby WCF hostované v rámci služby IIS. Tato funkce není ve výchozím nastavení povolená. Chcete-li jej povolit, je nutné přidat atribut `multipleSiteBindingsEnabled` do prvku <`serviceHostingEnvironment`> elementu v souboru Web. config a nastavit jej na `true`, jak je znázorněno v následujícím příkladu.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 Při hostování služby WCF v rámci služby IIS vytvoří služba IIS jednu základní adresu založenou na identifikátoru URI virtuálního adresáře, který obsahuje aplikaci. Pomocí Správce Internetová informační služba můžete přidat další základní adresy, které používají stejný protokol, a přidat na web jednu nebo více vazeb. U každé vazby zadejte protokol (HTTP nebo HTTPS), IP adresu, port a název hostitele. Další informace o použití Internetová informační služba Manageru najdete v tématu [Správce služby IIS (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753842(v=ws.10)). Další informace o přidávání vazeb do lokality najdete v tématu [Vytvoření webu (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772350(v=ws.10)) .  
  
 Zadání více základních adres pro stejnou lokalitu má vliv na obsah stránky s nápovědu WCF, import schématu a informace WSDL/MEX vygenerované službou. Stránka s nápovědě WCF zobrazí příkazový řádek, který se použije k vygenerování klienta WCF, který může komunikovat se službou. Tento příkazový řádek obsahuje pouze první adresu určenou ve vazbě služby IIS webu. Podobně při importu schématu je použita pouze první základní adresa zadaná ve vazbě služby IIS. Data WSDL a MEX obsahují všechny základní adresy zadané v vazbách služby IIS.  
  
> [!WARNING]
> To znamená, že pokud má služba dvě základní adresy, jednu pro interní uživatele a jednu pro externí uživatele, obě jsou uvedeny v informacích WSDL/MEX vygenerovaných službou.
