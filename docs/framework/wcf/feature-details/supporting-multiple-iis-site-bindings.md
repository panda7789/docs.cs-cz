---
title: "Podpora víc vazeb webu IIS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ebe433d1c18d46e0868f9566a273124e6bd63f1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="supporting-multiple-iis-site-bindings"></a>Podpora víc vazeb webu IIS
Při hostování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby v části Internetové informační služby (IIS) 7.0, můžete zadat více základní adresy, která používá stejný protokol ve stejné lokalitě. To umožňuje stejnou službu reagovat na několika různých identifikátory URI. To je užitečné, když chcete hostovat službu, která naslouchá na http://www.contoso.com a http://contoso.com. Je také užitečné k vytvoření služby, který má bázové adresy pro interní uživatele a samostatné základní adresa pro externí uživatele. Příklad: http://internal.contoso.com a http://www.contoso.com.  
  
> [!NOTE]
>  Tato funkce je dostupná, pomocí protokolu HTTP jenom.  
  
## <a name="multiple-base-addresses"></a>Vícenásobné základní adresy  
 Tato funkce je k dispozici pouze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, které jsou hostované v rámci služby IIS. Tato funkce není povolená ve výchozím nastavení. Povolit, je nutné přidat `multipleSiteBindingsEnabled` atribut <`serviceHostingEnvironment`> element v souboru Web.config souborů a nastavte ji na `true`, jak je znázorněno v následujícím příkladu.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 Při hostování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v rámci služby IIS, služba IIS vytvoří jednu základní adresu, na základě v identifikátoru URI do virtuálního adresáře, která obsahuje aplikaci. Můžete přidat další základní adresy, které používají stejný protokol pomocí Správce Internetové informační služby přidat jeden nebo více vazby na webové stránky. Pro každou vazbu zadejte protokol (HTTP nebo HTTPS), adresu IP, portu a názvu hostitele. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí Správce Internetové informační služby, najdete v tématu [Správce služby IIS (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]přidávání vazeb k lokalitě, najdete v části [vytvoření webového serveru (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Zadání více základní adresy pro stejnou lokalitu ovlivňuje obsah [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stránku nápovědy, import schématu a informace WSDL/MEX vygenerované službou. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Zobrazí příkazový řádek, který používá ke generování stránky nápovědy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, který může komunikovat se službou. Tento příkaz obsahuje pouze první adresa zadaná v vazby služby IIS pro web. Podobně když import schématu, pouze první základní adresu určenou v IIS vazby se používá. WSDL a MEX data obsahovat všechny základní adresami uvedenými v vazby služby IIS.  
  
> [!WARNING]
>  To znamená, že pokud služba má dvě základní adresy, jednu pro interní uživatele a druhou pro externí uživatele, jsou zadány oba ve schématu WSDL/MEX informace vygenerované službou.
