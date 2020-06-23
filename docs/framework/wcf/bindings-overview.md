---
title: Vazby ve Windows Communication Foundation – přehled
description: Seznamte se s vazbami, které určují, jak se připojit ke službě WCF, včetně prvků vazby a určení vazby pro koncový bod služby.
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: da8050c4e9aeb111de3a54315b3650bcf09f23ed
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247711"
---
# <a name="windows-communication-foundation-bindings-overview"></a>Vazby ve Windows Communication Foundation – přehled
Vazby jsou objekty, které slouží k zadání podrobností o komunikaci, které jsou požadovány pro připojení ke koncovému bodu služby Windows Communication Foundation (WCF). Každý koncový bod ve službě WCF vyžaduje, aby vazba byla dobře zadala. Toto téma popisuje typy informací o komunikaci, které definují vazby, prvky vazby, které vazby jsou součástí WCF a jak lze zadat vazbu pro koncový bod.  
  
## <a name="what-a-binding-defines"></a>Definice vazby  
 Informace ve vazbě mohou být velmi základní nebo velmi složité. Většina základních vazeb určuje pouze transportní protokol (například HTTP), který se musí použít pro připojení ke koncovému bodu. Obecně platí, že informace a vazba obsahuje informace o tom, jak připojit ke koncovému bodu spadá do jedné z následujících kategorií:  
  
 **Protokoly**  
 Určuje mechanismus zabezpečení, který se používá: buď spolehlivé možnosti zasílání zpráv, nebo nastavení toku kontextu transakce.  
  
 **Encoding**  
 Určuje kódování zprávy (například text nebo binární).  
  
 **Přenos**  
 Určuje podkladový transportní protokol, který se má použít (například TCP nebo HTTP).  
  
## <a name="the-elements-of-a-binding"></a>Prvky vazby  
 Vazba v podstatě sestává z uspořádaného zásobníku prvků vazby, z nichž každý určuje část informací o komunikaci požadovaných pro připojení ke koncovému bodu služby. Obě nejnižší vrstvy v zásobníku jsou nutné. V základu zásobníku je prvek vazby přenosu a těsně nad tímto prvkem, který obsahuje specifikace kódování zprávy. Volitelné prvky vazby, které určují jiné komunikační protokoly, jsou vrstveny nad těmito dvěma požadovanými prvky. Další informace o těchto prvcích vazby a jejich správném řazení naleznete v tématu [Custom Bindings](./extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 Informace ve vazbě mohou být složité a některá nastavení nemusí být kompatibilní s ostatními. Z tohoto důvodu WCF zahrnuje sadu vazeb poskytovaných systémem. Tyto vazby jsou navržené tak, aby pokryly většinu požadavků na aplikace. Následující třídy znázorňují některé příklady vazeb poskytovaných systémem:  
  
- <xref:System.ServiceModel.BasicHttpBinding>: Vazba protokolu HTTP vhodná pro připojení k webovým službám, které odpovídají specifikaci profilu WS-I Basic (například služby založené na webových službách ASP.NET).  
  
- <xref:System.ServiceModel.WSHttpBinding>: Interoperabilní vazba vhodná pro připojení ke koncovým bodům, které odpovídají protokolům WS-*.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: Používá .NET Framework pro připojení k jiným koncovým bodům WCF ve stejném počítači.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: Používá .NET Framework k vytvoření připojení zpráv ve frontě s ostatními koncovými body WCF.  

- <xref:System.ServiceModel.NetTcpBinding>: Tato vazba nabízí vyšší výkon než vazby HTTP a je ideální pro použití v místní síti.
  
 Úplný seznam s popisy všech vazeb poskytovaných službou WCF najdete v tématu [vazby poskytované systémem](system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Používání vlastních vazeb  
 Pokud žádná z obsažených vazeb poskytnutých systémem nemá správnou kombinaci funkcí, které vyžaduje aplikace služby, můžete vytvořit vlastní vazbu. Můžete to provést dvěma způsoby. Můžete buď vytvořit novou vazbu z existujících prvků vazby pomocí <xref:System.ServiceModel.Channels.CustomBinding> objektu, nebo můžete vytvořit plně definovanou vazbu odvozenou od <xref:System.ServiceModel.Channels.Binding> vazby. Další informace o vytváření vlastních vazeb pomocí těchto dvou přístupů najdete v tématech [vlastní vazby](./extending/custom-bindings.md) a [vytváření uživatelsky definovaných vazeb](./extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Použití vazeb  
 Použití vazeb zahrnuje dva základní kroky:  
  
1. Vyberte nebo definujte vazbu. Nejjednodušším způsobem je zvolit jednu ze systémových vazeb, které jsou součástí WCF, a použít je s jeho výchozím nastavením. Můžete také zvolit systémovou vazbu a obnovit její hodnoty vlastností tak, aby vyhovovaly vašim požadavkům. Alternativně můžete vytvořit vlastní vazbu nebo uživatelsky definovanou vazbu, která bude mít vyšší úroveň řízení a přizpůsobení.  
  
2. Vytvořte koncový bod, který používá vybranou nebo definovanou vazbu.  
  
## <a name="code-and-configuration"></a>Kód a konfigurace  
 Vazby můžete definovat dvěma způsoby: prostřednictvím kódu nebo prostřednictvím konfigurace. Tyto dva přístupy nezávisí na tom, zda používáte vazbu zadanou systémem nebo vlastní vazbou. Obecně platí, že použití kódu vám poskytne plnou kontrolu nad definicí vazby v době návrhu. Pomocí konfigurace na druhé straně umožňuje správce systému nebo uživateli služby nebo klienta WCF měnit parametry vazby bez nutnosti znovu kompilovat aplikaci služby. Tato flexibilita je často žádoucí, protože neexistuje žádný způsob, jak předpovědět konkrétní požadavky na počítač, na které se má nasadit aplikace WCF. Zachování informací o vazbě (a adresování) z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace. Všimněte si, že vazby definované v kódu jsou vytvořeny po vazbách určených v konfiguraci, což umožňuje, aby vazby definované kódem přepsaly jakékoli vazby definované konfigurací.  
  
## <a name="see-also"></a>Viz také

- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
