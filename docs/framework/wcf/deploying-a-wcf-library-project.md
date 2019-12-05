---
title: Nasazení projektu knihovny WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 186ce5ae3087fd9b4c7e5c32e110de4bc7d5e578
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801979"
---
# <a name="deploying-a-wcf-library-project"></a>Nasazení projektu knihovny WCF
Toto téma popisuje, jak lze nasadit projekt služby Windows Communication Foundation (WCF) Service Library.  
  
## <a name="deploying-a-wcf-service-library"></a>Nasazení knihovny služby WCF  
 Knihovna služby WCF je knihovna DLL (Dynamic-Link Library). V takovém případě jej nelze spustit samostatně. Je nutné ho nasadit do hostitelského prostředí. Další informace o tomto procesu najdete v tématu [hostování a využívání služeb WCF](https://docs.microsoft.com/previous-versions/dotnet/articles/bb332338(v=msdn.10)).  
  
 Knihovna služby WCF se dá nasadit jako jakákoli jiná služba WCF. Upozorňujeme však, že .NET Framework nepodporuje konfiguraci knihoven DLL. <xref:System.Configuration> podporuje jeden konfigurační soubor na doménu aplikace. Projekt knihovny služby WCF toto omezení řeší poskytnutím souboru App. config pro knihovnu během vývoje. Soubor App. config však není rozpoznán po nasazení.  
  
 Je nutné přesunout konfigurační kód do konfiguračního souboru rozpoznaného hostujícím prostředím. Pro samoobslužné hostování byste měli zkopírovat obsah souboru App. config do souboru App. config hostujícího spustitelného souboru. Pokud používáte službu IIS k hostování vaší služby, měli byste zkopírovat obsah souboru App. config do souboru Web. config virtuálního adresáře.
