---
title: Architektura programování aplikace služby
description: Pochopení architektury programování aplikací služby. Aplikace služby systému Windows jsou založeny na třídě, která dědí z typu System. ServiceProcess. ServiceBase.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
author: ghogen
ms.openlocfilehash: c59ccc5a8b2f11fda9c4734487092c1aabb74908
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925576"
---
# <a name="service-application-programming-architecture"></a>Architektura programování aplikace služby
Aplikace služby systému Windows jsou založeny na třídě, která dědí z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> třídy. Přepíšete metody z této třídy a definujte jejich funkčnost, abyste zjistili, jak se vaše služba chová.  
  
 K hlavním třídám, které se podílejí na tvorbě služby, patří:  
  
- <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>– Metody z třídy přepíšete <xref:System.ServiceProcess.ServiceBase> při vytváření služby a definováním kódu určíte, jak vaše služba funguje v této zděděné třídě.  
  
- <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType>a <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> – tyto třídy můžete použít k instalaci a odinstalaci služby.  
  
 Kromě toho třída s názvem <xref:System.ServiceProcess.ServiceController> lze použít k manipulaci s ní samotné služby. Tato třída se nezabývá vytvořením služby, ale je možné ji použít ke spuštění a zastavení služby, předání příkazů do ní a vrácení řady výčtů.  
  
## <a name="defining-your-services-behavior"></a>Definování chování vaší služby  
 Ve vaší třídě služby přepíšete funkce základní třídy, které určují, co se stane, když se ve Správci řízení služeb změní stav služby. <xref:System.ServiceProcess.ServiceBase>Třída zpřístupňuje následující metody, které lze přepsat pro přidání vlastního chování.  
  
|Metoda|Přepsat na|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Určete, jaké akce mají být provedeny při spuštění služby. Aby mohla služba provádět užitečnou práci, musíte v tomto postupu napsat kód.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Určete, co se má stát při pozastavení služby.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Určete, co se má stát, když se služba přestane spouštět.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Určete, co se má stát, když se služba po pozastavení pokračuje v normálním provozu.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Uveďte, co by mělo nastat před vypnutím systému, pokud je vaše služba v tuto chvíli spuštěná.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Určete, co se má stát, když vaše služba obdrží vlastní příkaz. Další informace o vlastních příkazech najdete v tématu MSDN online.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Určete, jak má služba reagovat při přijetí události řízení spotřeby, jako je například nízká baterie nebo pozastavená operace.|  
  
> [!NOTE]
> Tyto metody reprezentují stavy, během kterých se služba pohybuje v průběhu své životnosti. služba přejde z jednoho stavu na další. Například nikdy nebudete mít službu, aby reagovala na <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> příkaz před <xref:System.ServiceProcess.ServiceBase.OnStart%2A> voláním.  
  
 Existuje několik dalších vlastností a metod, které mají zájem. Mezi ně patří:  
  
- <xref:System.ServiceProcess.ServiceBase.Run%2A>Metoda <xref:System.ServiceProcess.ServiceBase> třídy. Toto je hlavní vstupní bod pro službu. Když vytvoříte službu pomocí šablony služby systému Windows, kód je vložen do metody vaší aplikace `Main` pro spuštění služby. Tento kód vypadá takto:  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    > V těchto příkladech se používá pole typu <xref:System.ServiceProcess.ServiceBase> , do kterého lze přidat každou službu, kterou vaše aplikace obsahuje, a poté lze všechny služby spustit společně. Pokud ale vytváříte jenom jednu službu, můžete se rozhodnout nepoužívat pole a jednoduše deklarovat nový objekt, který dědí <xref:System.ServiceProcess.ServiceBase> a pak ho spustí. Příklad naleznete v tématu [How to: Write Services Programs](how-to-write-services-programmatically.md).  
  
- Řada vlastností <xref:System.ServiceProcess.ServiceBase> třídy. Určují, jaké metody lze ve vaší službě volat. Například pokud <xref:System.ServiceProcess.ServiceBase.CanStop%2A> je vlastnost nastavena na `true` , <xref:System.ServiceProcess.ServiceBase.OnStop%2A> lze volat metodu ve vaší službě. Pokud <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> je vlastnost nastavena na `true` , <xref:System.ServiceProcess.ServiceBase.OnPause%2A> <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> lze volat metody a. Když nastavíte jednu z těchto vlastností na `true` , měli byste přepsat a definovat zpracování pro související metody.  
  
    > [!NOTE]
    > Vaše služba musí přinejmenším přepsat <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> být užitečná.  
  
 Můžete také použít komponentu s názvem <xref:System.ServiceProcess.ServiceController> ke komunikaci s a řízení chování existující služby.  
  
## <a name="see-also"></a>Viz také

- [Představení aplikací spouštěných jako služby systému Windows](introduction-to-windows-service-applications.md)
- [Postupy: Vytváření služeb systému Windows](how-to-create-windows-services.md)
