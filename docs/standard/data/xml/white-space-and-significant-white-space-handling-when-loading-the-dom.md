---
title: Zpracování mezer a významných mezer při načítání modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: 520d965737b82fda082aa44029f2a4042d948deb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281767"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Zpracování mezer a významných mezer při načítání modelu DOM
Při načítání dokumentu můžete nastavit možnost zachovat prázdné znaky a vytvořit uzly **XmlWhitespace** ve stromu dokumentu. Chcete-li vytvořit uzly s prázdným znakem, nastavte vlastnost **PreserveWhitespace** na hodnotu true. Pokud je vlastnost nastavena na **hodnotu false**, což je výchozí nastavení, nevytvoří se uzly s prázdným znakem. Významné uzly s bílým prostorem jsou vždy zachovány a uzly **XmlSignificantWhitespace** jsou vždy vytvořeny v paměti, aby představovaly tato data, a to bez ohledu na nastavení příznaku **PreserveWhitespace** .  
  
 Pokud je dokument načten z čtecího modulu, nastavení vlastnosti příznak **PreserveWhitespace** třídy **XmlDocument** má vliv na vytváření uzlů **XmlWhitespace** pouze v případě, že vlastnost **WhitespaceHandling** ve třídě **XmlTextReader** není nastavena na **WhitespaceHandling. None**. Jedná se o hodnotu vlastnosti **WhitespaceHandling** ve čtečce, která má přednost před nastavením tohoto příznaku v **XmlDocument**. Další informace o **XmlSignificantWhitespace**naleznete v tématu <xref:System.Xml.XmlSignificantWhitespace> .  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
