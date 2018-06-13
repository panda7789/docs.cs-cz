---
title: Odstranění uzlů z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec786564e6246f10e10d600f4822442884323557
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568456"
---
# <a name="removing-nodes-from-the-dom"></a>Odstranění uzlů z modelu DOM
Chcete-li odebrat uzel z XML modelu DOM (Document Object), použijte <xref:System.Xml.XmlNode.RemoveChild%2A> metoda odebrat konkrétní uzel. Při odebrání uzlu metoda odebere podstrom, které patří k uzlu odebírána; To znamená pokud není uzlem typu list.  
  
 Pokud chcete odstranit z modelu DOM více uzlů, použijte <xref:System.Xml.XmlNode.RemoveAll%2A> metoda odebrat všechny podřízené objekty a atributy, pokud je k dispozici, aktuální uzel.  
  
 Pokud pracujete s <xref:System.Xml.XmlNamedNodeMap>, můžete odebrat uzel pomocí <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metoda.  
  
 Chcete-li odebrat atributy, přečtěte si téma [odebrání atributů z uzlu elementu v modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
