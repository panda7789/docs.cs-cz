---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 91a29233d12a842a64b7d3dd497312f6dc6742ca
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423641"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplikace, které hostují obsah [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] přes PresentationHost. exe, implementují toto rozhraní, aby poskytovaly bod integrace mezi hostitelem a PresentationHost. exe.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikace, jako jsou například webové prohlížeče, mohou hostovat obsah WPF, včetně aplikací prohlížeče XAML (XBAP) a volně XAML. Pro hostování obsahu WPF [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikace vytvoří instanci [ovládacího prvku WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911). Aby bylo možné hostovat, WPF vytvoří instanci PresentationHost. exe, která poskytne hostovanému obsahu WPF na hostitele pro zobrazení v [ovládacím prvku WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).  
  
 Integrace povolená pomocí `IWpfHostSupport` umožňuje PresentationHost. exe:  
  
- Vyhledejte a zaregistrujte se nezpracovanými vstupními zařízeními (zařízení s lidskými rozhraními), na které má hostitelská aplikace zájem.  
  
- Přijímat vstupní zprávy z registrovaných nezpracovaných vstupních zařízení a předají příslušné zprávy do hostitelské aplikace.  
  
- Dotazování hostitelské aplikace na vlastní průběh a chybná uživatelská rozhraní.  
  
> [!NOTE]
> Toto rozhraní API je zamýšlené a podporované jenom pro použití v místním klientském počítači.  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|Umožňuje PresentationHost. exe zjistit nezpracované vstupní zařízení (zařízení s lidskými rozhraními), na které hostitelská aplikace zajímá.|  
|[FilterInputMessage](filterinputmessage.md)|Volá se PresentationHost. exe, když se přijme zpráva, pokud se nevrátí E_NOTIMPL.|  
|[GetCustomUI](getcustomui.md)|Ve výchozím nastavení poskytuje PresentationHost. exe vlastní průběh nasazení a uživatelská rozhraní chyby nasazení, která se zobrazí při nasazení obsahu WPF.|
