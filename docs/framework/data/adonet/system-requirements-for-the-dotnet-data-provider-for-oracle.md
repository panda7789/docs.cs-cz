---
title: Požadavky na systém pro zprostředkovatel dat .NET Framework pro Oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: a5ce0e831af40cbe86e6ac901d6e92d5a60f8774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Požadavky na systém pro zprostředkovatel dat .NET Framework pro Oracle
Zprostředkovatel dat .NET Framework pro Oracle vyžaduje Microsoft Data Access Components (MDAC) verze 2.6 nebo novější. Doporučuje se MDAC 2.8 SP1.  
  
 Musí mít také klienta Oracle 8i verze 3 (8.1.7) nebo novější.  
  
 Klientský software Oracle starší než verze Oracle 9i nemá přístup k UTF16 databáze, protože UTF16 je nová funkce v Oracle 9i. Chcete-li tuto funkci používat, je nutné upgradovat váš klientský software na Oracle 9i nebo novější.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Práce s poskytovatele dat Oracle a Data v kódování Unicode  
 Následuje seznam problémy související s Unicode, které byste měli zvážit při práci s zprostředkovatele dat .NET Framework pro Oracle a Oracle knihovny klienta. Další informace najdete v dokumentaci Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Nastavení hodnoty kódování Unicode v atribut připojovacího řetězce  
 Při práci s Oracle, můžete použít atribut připojovacího řetězce  
  
```  
Unicode=True   
```  
  
 k chybě při inicializaci knihovny klienta Oracle v režimu UTF-16. To způsobí, že klient Oracle knihovny tak, aby přijímal namísto řetězců vícebajtové znakové sady UTF-16 (což je velmi podobné UCS. 2). To umožňuje poskytovatel dat pro databázi Oracle vždy pracovat s jakoukoli stránku kódu Oracle bez další překlad práce. Tato konfigurace funguje jenom v případě Oracle 9i klienti používají ke komunikaci s databází Oracle 9i s alternativní znakovou sadu AL16UTF16. Pokud klienta Oracle 9i komunikuje se serverem 9i Oracle, jsou další prostředky požadované pro převod kódování Unicode **CommandText** hodnoty pro příslušné vícebajtové znakové sady, která Oracle9i server používá. Tím se vyhnout, když víte, že máte bezpečné konfiguraci přidáním `Unicode=True` připojovací řetězec.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Kombinování verze klienta Oracle a serveru Oracle  
 Oracle 8i klienti nemají přístup k **NCHAR**, **NVARCHAR2**, nebo **NCLOB** data do databáze Oracle 9i při serveru national znaková sada je zadán jako AL16UTF16 (na Výchozí nastavení pro Oracle 9i). Protože Podpora znakové sady UTF-16 nebyla zavedena dokud Oracle 9i, Oracle 8i klienti ji nemůže přečíst.  
  
### <a name="working-with-utf-8-data"></a>Práce s daty ve formátu UTF-8  
 Alternativní znaková sada, nastavte HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG klíč registru pro UTF8. Na vaši platformu pro další informace najdete v poznámkách k instalaci Oracle. Výchozí nastavení je primární znakovou sadu jazyka, ze kterého instalujete software klienta Oracle. Není nastavení jazyka tak, aby odpovídaly national jazyk znakovou sadu databázi, ke kterému se připojujete způsobí, že parametr a ve sloupci vazby odesílat nebo přijímat data v primární databázi znaková sada, není national znakovou sadu.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob může aktualizovat pouze úplná znaků.  
 Z důvodů použitelnost <xref:System.Data.OracleClient.OracleLob> objekt dědí z třídy rozhraní .NET Framework datového proudu a poskytuje **ReadByte** a **Metoda WriteByte** metody. Také implementuje metody, jako například **CopyTo** a **vymazat**, že pracovní na části Oracle **obchodní** objekty. Naproti tomu Oracle klientský software poskytuje několik rozhraní API pro práci s znak **obchodní**s (**datový typ CLOB** a **NCLOB**). Tato rozhraní API ale fungovat jenom úplné znaků. Vzhledem k tomuto rozdílu poskytovatele dat Oracle implementuje podporu **čtení** a **ReadByte** pracovat s daty ve formátu UTF-16 byte-wise způsobem. Ale jiné metody třídy **OracleLob** objektu povolit jenom úplné znak operace.  
  
## <a name="see-also"></a>Viz také  
 [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
