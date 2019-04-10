---
title: Vazby ve Windows Communication Foundation – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: c450de0eb3eead3a2d3b21c3635caa71d92ce07f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212801"
---
# <a name="windows-communication-foundation-bindings-overview"></a>Vazby ve Windows Communication Foundation – přehled
Vazby jsou objekty, které se používají k určení detaily komunikace, které jsou vyžadovány pro připojení ke koncovému bodu služby Windows Communication Foundation (WCF). Každý koncový bod služby WCF vyžaduje vazbu být správně zadaný. Toto téma popisuje typy komunikace – podrobnosti, které definují vazby elementy vazby, které vazby jsou součástí WCF a jak vazbu se dá nastavit pro koncový bod.  
  
## <a name="what-a-binding-defines"></a>Co definuje vazbu  
 Informace v vazbu může být velmi základní nebo velmi složité. Základní vazby určuje pouze přenosový protokol (například HTTP), který se použije pro připojení ke koncovému bodu. Obecně platí informace, které obsahuje vazbu o tom, jak připojit ke koncovému bodu spadá do jedné z těchto kategorií.  
  
 Protokoly  
 Určuje mechanismus zabezpečení, který se používá: funkce spolehlivé zasílání zpráv nebo nastavení toku kontextu transakce.  
  
 Kódování  
 Určuje kódování zpráv (například text nebo binární).  
  
 Přenos  
 Určuje základní přenos protokol, který použít (například protokol TCP nebo HTTP).  
  
## <a name="the-elements-of-a-binding"></a>Prvky vazby  
 Vazbu v podstatě se skládá ze seřazené zásobníku vazby prvky, z nichž každý určuje součástí komunikační informace požadované pro připojení ke koncovému bodu služby. Dvě nejnižší vrstvy v zásobníku jsou povinné. Přímo nad tím je prvek, který obsahuje zprávu kódování specifikace základní zásobníku je element vazby přenosu. Volitelné vazby prvky, které určují komunikační protokoly jsou rozloženy do vrstev nad tyto dva požadované prvky. Další informace o těchto elementů vazby a správné řazení, naleznete v tématu [vlastní vazby](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 Informace v vazbu může být složité a některá nastavení nemusí být kompatibilní s ostatními. Z tohoto důvodu WCF obsahuje sadu vazeb poskytovaných systémem. Tyto vazby jsou navržené tak, aby pokryl většinu požadavků aplikace. Následující třídy představují některé příklady vazeb poskytovaných systémem:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: Protokol HTTP vazby vhodné pro připojení k webovým službám, který odpovídá WS-I Basic Profile specification (například webové služby technologie ASP.NET na základě služby).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Interoperabilní vazbu vhodný pro připojení ke koncovým bodům, které odpovídají WS-* protokoly.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Používá [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pro připojení k jiné koncových bodů WCF na stejném počítači.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Používá [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] k vytvoření zprávy ve frontě připojení pomocí dalších koncových bodů WCF.  

- <xref:System.ServiceModel.NetTcpBinding>: Tato vazba nabízí vyšší výkon než vazby protokolu HTTP a je ideální pro použití v místní síti.
  
 Úplný seznam najdete popisy všech WCF vazeb poskytovaných systémem, naleznete v tématu [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Použití vlastní vazby  
 Pokud žádný z vazeb poskytovaných systémem zahrnuté nemá správné kombinace funkce, které vyžaduje služby aplikace, můžete vytvořit vlastní vazby. Existují dva způsoby, jak to provést. Můžete vytvořit novou vazbu v dříve existujícím elementů vazby pomocí <xref:System.ServiceModel.Channels.CustomBinding> objektu nebo můžete vytvořit zcela uživatelem definované vazby odvozením z <xref:System.ServiceModel.Channels.Binding> vazby. Další informace o vytvoření vlastní vazby pomocí těchto dvou přístupů najdete v tématu [vlastní vazby](../../../docs/framework/wcf/extending/custom-bindings.md) a [Creating User-Defined vazby](../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Používání vazeb  
 Používání vazeb zahrnuje dva základní kroky:  
  
1.  Vyberte nebo definujících vazbu. Nejjednodušší způsob je zvolte jednu z vazeb poskytovaných systémem, který je součástí WCF a jeho použití s výchozím nastavením. Můžete také zvolit vazeb poskytovaných systémem a obnovit jeho hodnotám vlastností tak, aby vyhovoval vašim požadavkům. Alternativně můžete vytvořit vlastní vazby nebo vazbu definované uživatelem mají vyšší stupeň řízení a přizpůsobení.  
  
2.  Vytvoření koncového bodu, který používá vazbu vybrané nebo definované.  
  
## <a name="code-and-configuration"></a>Kódu a konfigurace  
 Můžete definovat vazby dvěma způsoby: prostřednictvím kódu nebo konfigurace. Tyto dva přístupy nebyly závislé na tom, jestli používáte vazeb poskytovaných systémem nebo vlastní vazby. Obecně platí pomocí kódu vám plnou kontrolu nad definice vazby v době návrhu. Použití konfigurace, umožňuje na druhé straně může správce systému nebo uživatele služby WCF nebo klienta můžete změnit parametry vazby bez nutnosti znovu kompilovat aplikace služby. Díky této flexibilitě je často žádoucí, protože neexistuje žádný způsob, jak předvídat požadavky na konkrétní počítač, na kterých aplikace WCF je k nasazení. Vazba (a adresování) informace z kódu umožňuje změnit bez nutnosti rekompilace nebo opětovného nasazení aplikace. Všimněte si, že se po vazby zadaný v konfiguraci, umožňuje kódu definované vazby pro přepsání jakékoli konfigurace definované vazby vytvoří vazeb definovaných v kódu.  
  
## <a name="see-also"></a>Viz také:

- [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
