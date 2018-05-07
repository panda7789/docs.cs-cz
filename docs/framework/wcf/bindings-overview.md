---
title: Vazby ve Windows Communication Foundation – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: 38661c2ca0e3329f508e2740dfcdf69c0d5e4105
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="windows-communication-foundation-bindings-overview"></a>Vazby ve Windows Communication Foundation – přehled
Vazby jsou objekty, které se používají a zadejte podrobnosti komunikace, které jsou potřebné pro připojení ke koncovému bodu služby Windows Communication Foundation (WCF). Každý koncový bod v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služba vyžaduje, aby vazba být správně zadaný. Toto téma popisuje typy komunikace – podrobnosti definující vazby elementů vazby, které vazby jsou součástí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], a jak lze zadat vazbu pro koncový bod.  
  
## <a name="what-a-binding-defines"></a>Co definuje vazbu  
 Informace v vazbu může být velmi základní nebo velmi složité. Nejzákladnější vazba určuje pouze přenosový protokol (jako je například HTTP), musíte použít pro připojení ke koncovému bodu. Obecně platí informace, které obsahuje vazbu o tom, jak připojit ke koncovému bodu spadá do jedné z následujících kategorií.  
  
 protokoly  
 Určuje používá mechanismus zabezpečení: spolehlivého zasílání zpráv schopností nebo nastavení tok kontextu transakce.  
  
 Kódování  
 Určuje kódování zpráv (například textu nebo binárních).  
  
 Přenos  
 Určuje základní přenosový protokol použít (například protokol TCP nebo HTTP).  
  
## <a name="the-elements-of-a-binding"></a>Prvky vazby  
 Vazba v podstatě se skládá ze seřazené zásobníku vazby prvky, z nichž každý určuje součástí komunikační informace požadované pro připojení ke koncovému bodu služby. Dvě nejnižší vrstvy v zásobníku se vyžaduje. Nad touto je elementu, který obsahuje zprávu kódování specifikace na bázi zásobníku je element vazby přenosu. Prvky volitelné vazby, které zadejte komunikační protokoly jsou vrstvu nad tyto dvě požadované prvky. Další informace o tyto prvky vazby a jejich správné řazení najdete v tématu [vlastní vazby](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 Informace v vazbu může být složité a některá nastavení nemusí být kompatibilní s ostatními. Z tohoto důvodu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zahrnuje sadu vazby poskytované systémem. Tyto vazby jsou navrženy tak, aby pokrývalo většina požadavky aplikací. Následující třídy představují některé příklady vazby poskytované systémem:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: HTTP protokol vazby vhodný pro připojení k webovým službám, který odpovídá WS-I Basic Profile specification (například webové služby technologie ASP.NET založeného na službách).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Umožňuje vzájemnou spolupráci vazbu vhodný pro připojení ke koncovým bodům, které odpovídají WS-* protokoly.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Používá [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] se připojit k jiné [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] koncových bodů na stejném počítači.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Používá [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] k vytvoření připojení zpráv zařazených ve frontě s jinými [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] koncové body.  
  
 Úplný seznam, s popisy, všechny [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-zadaný vazby, najdete v části [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Použití vlastní vazby  
 Pokud žádný z vazby poskytované systémem zahrnuté nemá správnou kombinaci funkcí, které vyžaduje aplikaci služby, můžete vytvořit vlastní vazby. Chcete-li to provést dvěma způsoby. Můžete buď vytvořit novou vazbu z existující elementů vazby pomocí <xref:System.ServiceModel.Channels.CustomBinding> objekt nebo můžete vytvořit vazbu úplně uživatelem definované odvozené z <xref:System.ServiceModel.Channels.Binding> vazby. Další informace o vytvoření vlastní vazby pomocí tyto dva přístupy, najdete v části [vlastní vazby](../../../docs/framework/wcf/extending/custom-bindings.md) a [Creating User-Defined vazby](../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Používání vazeb  
 Používání vazeb zahrnuje dva základní kroky:  
  
1.  Vyberte nebo zadejte vazbu. Nejsnazší je vyberte jednu z vazby poskytované systémem, který je součástí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a jeho použití s jeho výchozí nastavení. Můžete také zvolit vazby poskytované systémem a obnovit jeho hodnoty vlastností podle svých potřeb. Alternativně můžete vytvořit vlastní vazby nebo uživatelem definované vazby má vyšší stupňů řízení a přizpůsobení.  
  
2.  Vytvořte koncový bod, který používá vazby vybrané nebo definován.  
  
## <a name="code-and-configuration"></a>Kód a konfigurace  
 Můžete definovat vazby dvěma způsoby: pomocí kódu nebo prostřednictvím konfigurace. Tyto dva přístupy nezávisí na tom, jestli používáte vazby poskytované systémem nebo vlastní vazby. Obecně platí pomocí kódu, poskytuje úplnou kontrolu nad definici vazby v době návrhu. Použití konfigurace na druhé straně umožňuje správce systému nebo uživatel [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služba nebo klienta ke změně parametrů vazby bez nutnosti její kompilace aplikace služby. Tuto flexibilitu potřebují je často žádoucí, protože neexistuje žádný způsob, jak předvídání požadavků konkrétní počítač, na kterém [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace je k nasazení. Informace o zachování vazby (a adresování) kód vám umožní se změnit bez nutnosti rekompilace nebo opětovného nasazení aplikace. Všimněte si, že vazeb definovaných v kódu jsou vytvořeny po vazby zadaný v konfiguraci, povolení definované kód vazby přepsat všechny konfigurace definované vazby.  
  
## <a name="see-also"></a>Viz také  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
