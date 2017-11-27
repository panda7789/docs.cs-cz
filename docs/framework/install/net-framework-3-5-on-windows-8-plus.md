---
title: "Nainstalujte rozhraní .NET Framework 3.5 ve Windows 8, Windows 8.1 a Windows 10"
ms.date: 05/26/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework 3.5, installing on Windows 8
- Windows 8, installing .NET Framework 3.5
ms.assetid: 3eab3eb4-4573-42ac-98f8-36fb2c22c7d5
caps.latest.revision: "69"
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9c8dcfacff689761d9ec891db8a1a4756acece0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="install-the-net-framework-35-on-windows-8-windows-81-and-windows-10"></a>Nainstalujte rozhraní .NET Framework 3.5 ve Windows 8, Windows 8.1 a Windows 10

Rozhraní .NET Framework je nedílnou součástí mnoho aplikace běžící v systému Windows a poskytuje běžné funkce pro tyto aplikace spouštět. Pro vývojáře rozhraní .NET Framework poskytuje konzistentní programovací model pro vytváření aplikací. Pokud používáte operační systém Windows, rozhraní .NET Framework může být již nainstalován ve vašem počítači. Konkrétně [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] je součástí [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] je součástí [!INCLUDE[win81](../../../includes/win81-md.md)]a [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] je součástí Windows 10.  
  
Rozhraní .NET Framework 3.5, ale není automaticky instalován se [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], nebo Windows 10 a ke spuštění aplikace, které na ní závisí musí být samostatně povolen. K tomu musí dojít prostřednictvím Windows Update, což je volána v jednom ze tří způsobů. Všechny tyto vyžadovat připojení k Internetu:  
  
- [Na požádání nainstalovat rozhraní .NET Framework 3.5](#OnDemand)  
  
- [Povolení rozhraní .NET Framework 3.5 v Ovládacích panelech](#ControlPanel)  
  
- [Stáhnout instalační program rozhraní .NET Framework 3.5](http://www.microsoft.com/en-us/download/details.aspx?id=21) (Poznámka: Tato nestáhne rozhraní .NET Framework přímo, je instalační program, který vyvolá Windows Update.)  
  
Během instalace, se můžete setkat chyba 0x800f0906, 0x800f0907 nebo 0x800f081f, v takovém případě odkazovat na [chyby instalace rozhraní .NET Framework 3.5: 0x800f0906, 0x800f0907 nebo 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09). Všimněte si, že tyto může být vyřešen instalací [aktualizaci zabezpečení 3005628](https://support.microsoft.com/kb/3005628).  
  
Pokud některou z výše uvedených metod selže nebo pokud nemáte připojení k Internetu, je třeba použít instalačním médiu systému Windows. Podrobnosti najdete v tématu metoda 3 podle chyby 0x800f0906 [článek Chyba instalace rozhraní .NET Framework 3.5](https://support.microsoft.com/en-us/kb/2734782). Pokud nemáte instalačního média, najdete v části [vytvořit instalační médium pro Windows 8.1](http://windows.microsoft.com/en-US/windows-8/create-reset-refresh-media?woldogcb=0).  
  
**Důležité poznámky:**
  
- Obecně platí nemusíte odinstalovat všechny verze rozhraní .NET Framework z vašeho počítače. Různé aplikace závisí na různých verzích rozhraní a více verzí rozhraní .NET Framework mohou společně existovat v jednom počítači ve stejnou dobu.  
  
- Rozhraní .NET Framework 3.5 také používá aplikace vytvořené pro verze 2.0 a 3.0.  
  
- Instalace jazykové sady systému Windows před instalací rozhraní .NET Framework 3.5 může způsobit selhání instalace rozhraní .NET Framework 3.5. Nainstalujte rozhraní .NET Framework 3.5 před instalací všechny jazykové sady systému Windows.  
  
- Služba Windows CardSpace není k dispozici v rozhraní .NET Framework 3.5 na [!INCLUDE[win8](../../../includes/win8-md.md)].  
  
- Z důvodu komplikace kolem instalovaných rozhraní .NET Framework 3.5 je bohužel není možné zajistit samostatné, samostatný instalační program, který můžete spustit nezávisle na služby Windows Update. Pokud selžou všechny ostatní metody, je nutné uchýlit na instalačním médiu jak bylo popsáno výše.  
  
<a name="OnDemand"></a>   
## <a name="install-the-net-framework-35-on-demand"></a>Na požádání nainstalovat rozhraní .NET Framework 3.5

Pokud aplikace vyžaduje rozhraní .NET Framework 3.5, ale nenajde této verze povolen v počítači, zobrazí pole následující zpráva při instalaci nebo při prvním spuštění aplikace. V okně, vyberte **nainstalujte tuto funkci** povolení rozhraní .NET Framework 3.5. Tato možnost vyžaduje připojení k Internetu.  
  
![Dialogové okno pro 3.5 instalace v systému Windows 8](../../../docs/framework/deployment/media/installdialog.png "installdialog")  
  
<a name="ControlPanel"></a>   
## <a name="enable-the-net-framework-35-in-control-panel"></a>Povolení rozhraní .NET Framework 3.5 v Ovládacích panelech

Můžete povolit rozhraní .NET Framework 3.5 pomocí ovládacích panelů. Tato možnost vyžaduje připojení k Internetu.  
  
1. Stiskněte klávesu Windows ![s logem Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici. Zadejte "Funkce systému Windows" a stiskněte klávesu Enter. Po výběru této možnosti **Windows zapnout nebo vypnout funkce** dialogové okno. Případně, otevřete ovládací panely, klikněte na **programy** položky a potom vyberte **Windows zapnout nebo vypnout funkce** pod **programy a funkce**.  
  
2. Vyberte **rozhraní .NET Framework 3.5 (zahrnuje rozhraní .NET 2.0 a 3.0)** zaškrtněte políčko **OK**a pokud se zobrazí výzva, restartujte počítač.  
  
Není třeba vybírat podřízené položky pro **aktivace Windows Communication Foundation (WCF) HTTP** Pokud si nejste vývojáři, který vyžaduje skript WCF a funkce mapování obslužné rutiny.
  
## <a name="see-also"></a>Viz také

[Průvodce instalací](../../../docs/framework/get-started/index.md)
