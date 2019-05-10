---
title: Kolekce schémat OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6c3441e86d4c5267418cf8002ba17d539c464d5c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645901"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="5684c-102">Kolekce schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="5684c-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="5684c-103">Tato část popisuje kolekci podpora schématu pro zprostředkovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="5684c-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="5684c-104">Zprostředkovatel Microsoft SQL serveru OLE DB</span><span class="sxs-lookup"><span data-stu-id="5684c-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="5684c-105">Microsoft SQL Server OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="5684c-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="5684c-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="5684c-106">Tables</span></span>  
  
- <span data-ttu-id="5684c-107">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-107">Columns</span></span>  
  
- <span data-ttu-id="5684c-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="5684c-108">Procedures</span></span>  
  
- <span data-ttu-id="5684c-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5684c-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="5684c-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="5684c-110">Catalog</span></span>  
  
- <span data-ttu-id="5684c-111">Indexy</span><span class="sxs-lookup"><span data-stu-id="5684c-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="5684c-112">Tabulky</span><span class="sxs-lookup"><span data-stu-id="5684c-112">Tables</span></span>  
  
|<span data-ttu-id="5684c-113">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-113">ColumnName</span></span>|<span data-ttu-id="5684c-114">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-115">TABLE_CATALOG</span></span>|<span data-ttu-id="5684c-116">String</span><span class="sxs-lookup"><span data-stu-id="5684c-116">String</span></span>|  
|<span data-ttu-id="5684c-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="5684c-118">String</span><span class="sxs-lookup"><span data-stu-id="5684c-118">String</span></span>|  
|<span data-ttu-id="5684c-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-119">TABLE_NAME</span></span>|<span data-ttu-id="5684c-120">String</span><span class="sxs-lookup"><span data-stu-id="5684c-120">String</span></span>|  
|<span data-ttu-id="5684c-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-121">TABLE_TYPE</span></span>|<span data-ttu-id="5684c-122">String</span><span class="sxs-lookup"><span data-stu-id="5684c-122">String</span></span>|  
|<span data-ttu-id="5684c-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-123">TABLE_GUID</span></span>|<span data-ttu-id="5684c-124">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-124">Guid</span></span>|  
|<span data-ttu-id="5684c-125">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-125">DESCRIPTION</span></span>|<span data-ttu-id="5684c-126">String</span><span class="sxs-lookup"><span data-stu-id="5684c-126">String</span></span>|  
|<span data-ttu-id="5684c-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="5684c-127">TABLE_PROPID</span></span>|<span data-ttu-id="5684c-128">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-128">Int64</span></span>|  
|<span data-ttu-id="5684c-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5684c-129">DATE_CREATED</span></span>|<span data-ttu-id="5684c-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-130">DateTime</span></span>|  
|<span data-ttu-id="5684c-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5684c-131">DATE_MODIFIED</span></span>|<span data-ttu-id="5684c-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="5684c-133">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-133">Columns</span></span>  
  
|<span data-ttu-id="5684c-134">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-134">ColumnName</span></span>|<span data-ttu-id="5684c-135">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-136">TABLE_CATALOG</span></span>|<span data-ttu-id="5684c-137">String</span><span class="sxs-lookup"><span data-stu-id="5684c-137">String</span></span>|  
|<span data-ttu-id="5684c-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="5684c-139">String</span><span class="sxs-lookup"><span data-stu-id="5684c-139">String</span></span>|  
|<span data-ttu-id="5684c-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-140">TABLE_NAME</span></span>|<span data-ttu-id="5684c-141">String</span><span class="sxs-lookup"><span data-stu-id="5684c-141">String</span></span>|  
|<span data-ttu-id="5684c-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-142">COLUMN_NAME</span></span>|<span data-ttu-id="5684c-143">String</span><span class="sxs-lookup"><span data-stu-id="5684c-143">String</span></span>|  
|<span data-ttu-id="5684c-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-144">COLUMN_GUID</span></span>|<span data-ttu-id="5684c-145">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-145">Guid</span></span>|  
|<span data-ttu-id="5684c-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5684c-146">COLUMN_PROPID</span></span>|<span data-ttu-id="5684c-147">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-147">Int64</span></span>|  
|<span data-ttu-id="5684c-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5684c-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="5684c-149">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-149">Int64</span></span>|  
|<span data-ttu-id="5684c-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5684c-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="5684c-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-151">Boolean</span></span>|  
|<span data-ttu-id="5684c-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5684c-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="5684c-153">String</span><span class="sxs-lookup"><span data-stu-id="5684c-153">String</span></span>|  
|<span data-ttu-id="5684c-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5684c-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="5684c-155">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-155">Int64</span></span>|  
|<span data-ttu-id="5684c-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5684c-156">IS_NULLABLE</span></span>|<span data-ttu-id="5684c-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-157">Boolean</span></span>|  
|<span data-ttu-id="5684c-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-158">DATA_TYPE</span></span>|<span data-ttu-id="5684c-159">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-159">Int32</span></span>|  
|<span data-ttu-id="5684c-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-160">TYPE_GUID</span></span>|<span data-ttu-id="5684c-161">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-161">Guid</span></span>|  
|<span data-ttu-id="5684c-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5684c-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5684c-163">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-163">Int64</span></span>|  
|<span data-ttu-id="5684c-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5684c-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5684c-165">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-165">Int64</span></span>|  
|<span data-ttu-id="5684c-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5684c-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5684c-167">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-167">Int32</span></span>|  
|<span data-ttu-id="5684c-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5684c-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="5684c-169">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-169">Int16</span></span>|  
|<span data-ttu-id="5684c-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5684c-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="5684c-171">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-171">Int64</span></span>|  
|<span data-ttu-id="5684c-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="5684c-173">String</span><span class="sxs-lookup"><span data-stu-id="5684c-173">String</span></span>|  
|<span data-ttu-id="5684c-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="5684c-175">String</span><span class="sxs-lookup"><span data-stu-id="5684c-175">String</span></span>|  
|<span data-ttu-id="5684c-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="5684c-177">String</span><span class="sxs-lookup"><span data-stu-id="5684c-177">String</span></span>|  
|<span data-ttu-id="5684c-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="5684c-179">String</span><span class="sxs-lookup"><span data-stu-id="5684c-179">String</span></span>|  
|<span data-ttu-id="5684c-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="5684c-181">String</span><span class="sxs-lookup"><span data-stu-id="5684c-181">String</span></span>|  
|<span data-ttu-id="5684c-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-182">COLLATION_NAME</span></span>|<span data-ttu-id="5684c-183">String</span><span class="sxs-lookup"><span data-stu-id="5684c-183">String</span></span>|  
|<span data-ttu-id="5684c-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="5684c-185">String</span><span class="sxs-lookup"><span data-stu-id="5684c-185">String</span></span>|  
|<span data-ttu-id="5684c-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="5684c-187">String</span><span class="sxs-lookup"><span data-stu-id="5684c-187">String</span></span>|  
|<span data-ttu-id="5684c-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-188">DOMAIN_NAME</span></span>|<span data-ttu-id="5684c-189">String</span><span class="sxs-lookup"><span data-stu-id="5684c-189">String</span></span>|  
|<span data-ttu-id="5684c-190">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-190">DESCRIPTION</span></span>|<span data-ttu-id="5684c-191">String</span><span class="sxs-lookup"><span data-stu-id="5684c-191">String</span></span>|  
|<span data-ttu-id="5684c-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="5684c-192">COLUMN_LCID</span></span>|<span data-ttu-id="5684c-193">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-193">Int32</span></span>|  
|<span data-ttu-id="5684c-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="5684c-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="5684c-195">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-195">Int32</span></span>|  
|<span data-ttu-id="5684c-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="5684c-196">COLUMN_SORTID</span></span>|<span data-ttu-id="5684c-197">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-197">Int32</span></span>|  
|<span data-ttu-id="5684c-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="5684c-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="5684c-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="5684c-199">Byte[]</span></span>|  
|<span data-ttu-id="5684c-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="5684c-200">IS_COMPUTED</span></span>|<span data-ttu-id="5684c-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="5684c-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="5684c-202">Procedures</span></span>  
  
|<span data-ttu-id="5684c-203">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-203">ColumnName</span></span>|<span data-ttu-id="5684c-204">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5684c-206">String</span><span class="sxs-lookup"><span data-stu-id="5684c-206">String</span></span>|  
|<span data-ttu-id="5684c-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5684c-208">String</span><span class="sxs-lookup"><span data-stu-id="5684c-208">String</span></span>|  
|<span data-ttu-id="5684c-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="5684c-210">String</span><span class="sxs-lookup"><span data-stu-id="5684c-210">String</span></span>|  
|<span data-ttu-id="5684c-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5684c-212">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-212">Int16</span></span>|  
|<span data-ttu-id="5684c-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5684c-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="5684c-214">String</span><span class="sxs-lookup"><span data-stu-id="5684c-214">String</span></span>|  
|<span data-ttu-id="5684c-215">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-215">DESCRIPTION</span></span>|<span data-ttu-id="5684c-216">String</span><span class="sxs-lookup"><span data-stu-id="5684c-216">String</span></span>|  
|<span data-ttu-id="5684c-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5684c-217">DATE_CREATED</span></span>|<span data-ttu-id="5684c-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-218">DateTime</span></span>|  
|<span data-ttu-id="5684c-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5684c-219">DATE_MODIFIED</span></span>|<span data-ttu-id="5684c-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="5684c-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5684c-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="5684c-222">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-222">ColumnName</span></span>|<span data-ttu-id="5684c-223">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5684c-225">String</span><span class="sxs-lookup"><span data-stu-id="5684c-225">String</span></span>|  
|<span data-ttu-id="5684c-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5684c-227">String</span><span class="sxs-lookup"><span data-stu-id="5684c-227">String</span></span>|  
|<span data-ttu-id="5684c-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="5684c-229">String</span><span class="sxs-lookup"><span data-stu-id="5684c-229">String</span></span>|  
|<span data-ttu-id="5684c-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-230">PARAMETER_NAME</span></span>|<span data-ttu-id="5684c-231">String</span><span class="sxs-lookup"><span data-stu-id="5684c-231">String</span></span>|  
|<span data-ttu-id="5684c-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5684c-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="5684c-233">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-233">Int32</span></span>|  
|<span data-ttu-id="5684c-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="5684c-235">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-235">Int32</span></span>|  
|<span data-ttu-id="5684c-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5684c-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="5684c-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-237">Boolean</span></span>|  
|<span data-ttu-id="5684c-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5684c-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="5684c-239">String</span><span class="sxs-lookup"><span data-stu-id="5684c-239">String</span></span>|  
|<span data-ttu-id="5684c-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5684c-240">IS_NULLABLE</span></span>|<span data-ttu-id="5684c-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-241">Boolean</span></span>|  
|<span data-ttu-id="5684c-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-242">DATA_TYPE</span></span>|<span data-ttu-id="5684c-243">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-243">Int32</span></span>|  
|<span data-ttu-id="5684c-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5684c-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5684c-245">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-245">Int64</span></span>|  
|<span data-ttu-id="5684c-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5684c-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5684c-247">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-247">Int64</span></span>|  
|<span data-ttu-id="5684c-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5684c-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5684c-249">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-249">Int32</span></span>|  
|<span data-ttu-id="5684c-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5684c-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="5684c-251">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-251">Int16</span></span>|  
|<span data-ttu-id="5684c-252">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-252">DESCRIPTION</span></span>|<span data-ttu-id="5684c-253">String</span><span class="sxs-lookup"><span data-stu-id="5684c-253">String</span></span>|  
|<span data-ttu-id="5684c-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-254">TYPE_NAME</span></span>|<span data-ttu-id="5684c-255">String</span><span class="sxs-lookup"><span data-stu-id="5684c-255">String</span></span>|  
|<span data-ttu-id="5684c-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="5684c-257">String</span><span class="sxs-lookup"><span data-stu-id="5684c-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="5684c-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="5684c-258">Catalog</span></span>  
  
|<span data-ttu-id="5684c-259">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-259">ColumnName</span></span>|<span data-ttu-id="5684c-260">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-261">CATALOG_NAME</span></span>|<span data-ttu-id="5684c-262">String</span><span class="sxs-lookup"><span data-stu-id="5684c-262">String</span></span>|  
|<span data-ttu-id="5684c-263">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-263">DESCRIPTION</span></span>|<span data-ttu-id="5684c-264">String</span><span class="sxs-lookup"><span data-stu-id="5684c-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="5684c-265">Indexy</span><span class="sxs-lookup"><span data-stu-id="5684c-265">Indexes</span></span>  
  
|<span data-ttu-id="5684c-266">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-266">ColumnName</span></span>|<span data-ttu-id="5684c-267">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-268">TABLE_CATALOG</span></span>|<span data-ttu-id="5684c-269">String</span><span class="sxs-lookup"><span data-stu-id="5684c-269">String</span></span>|  
|<span data-ttu-id="5684c-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="5684c-271">String</span><span class="sxs-lookup"><span data-stu-id="5684c-271">String</span></span>|  
|<span data-ttu-id="5684c-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-272">TABLE_NAME</span></span>|<span data-ttu-id="5684c-273">String</span><span class="sxs-lookup"><span data-stu-id="5684c-273">String</span></span>|  
|<span data-ttu-id="5684c-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-274">INDEX_CATALOG</span></span>|<span data-ttu-id="5684c-275">String</span><span class="sxs-lookup"><span data-stu-id="5684c-275">String</span></span>|  
|<span data-ttu-id="5684c-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="5684c-277">String</span><span class="sxs-lookup"><span data-stu-id="5684c-277">String</span></span>|  
|<span data-ttu-id="5684c-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-278">INDEX_NAME</span></span>|<span data-ttu-id="5684c-279">String</span><span class="sxs-lookup"><span data-stu-id="5684c-279">String</span></span>|  
|<span data-ttu-id="5684c-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="5684c-280">PRIMARY_KEY</span></span>|<span data-ttu-id="5684c-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-281">Boolean</span></span>|  
|<span data-ttu-id="5684c-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="5684c-282">UNIQUE</span></span>|<span data-ttu-id="5684c-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-283">Boolean</span></span>|  
|<span data-ttu-id="5684c-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="5684c-284">CLUSTERED</span></span>|<span data-ttu-id="5684c-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-285">Boolean</span></span>|  
|<span data-ttu-id="5684c-286">TYP</span><span class="sxs-lookup"><span data-stu-id="5684c-286">TYPE</span></span>|<span data-ttu-id="5684c-287">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-287">Int32</span></span>|  
|<span data-ttu-id="5684c-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="5684c-288">FILL_FACTOR</span></span>|<span data-ttu-id="5684c-289">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-289">Int32</span></span>|  
|<span data-ttu-id="5684c-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="5684c-290">INITIAL_SIZE</span></span>|<span data-ttu-id="5684c-291">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-291">Int32</span></span>|  
|<span data-ttu-id="5684c-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="5684c-292">NULLS</span></span>|<span data-ttu-id="5684c-293">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-293">Int32</span></span>|  
|<span data-ttu-id="5684c-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="5684c-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="5684c-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-295">Boolean</span></span>|  
|<span data-ttu-id="5684c-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="5684c-296">AUTO_UPDATE</span></span>|<span data-ttu-id="5684c-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-297">Boolean</span></span>|  
|<span data-ttu-id="5684c-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="5684c-298">NULL_COLLATION</span></span>|<span data-ttu-id="5684c-299">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-299">Int32</span></span>|  
|<span data-ttu-id="5684c-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5684c-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="5684c-301">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-301">Int64</span></span>|  
|<span data-ttu-id="5684c-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-302">COLUMN_NAME</span></span>|<span data-ttu-id="5684c-303">String</span><span class="sxs-lookup"><span data-stu-id="5684c-303">String</span></span>|  
|<span data-ttu-id="5684c-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-304">COLUMN_GUID</span></span>|<span data-ttu-id="5684c-305">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-305">Guid</span></span>|  
|<span data-ttu-id="5684c-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5684c-306">COLUMN_PROPID</span></span>|<span data-ttu-id="5684c-307">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-307">Int64</span></span>|  
|<span data-ttu-id="5684c-308">KOLACE</span><span class="sxs-lookup"><span data-stu-id="5684c-308">COLLATION</span></span>|<span data-ttu-id="5684c-309">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-309">Int16</span></span>|  
|<span data-ttu-id="5684c-310">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="5684c-310">CARDINALITY</span></span>|<span data-ttu-id="5684c-311">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="5684c-311">Decimal</span></span>|  
|<span data-ttu-id="5684c-312">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="5684c-312">PAGES</span></span>|<span data-ttu-id="5684c-313">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-313">Int32</span></span>|  
|<span data-ttu-id="5684c-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="5684c-314">FILTER_CONDITION</span></span>|<span data-ttu-id="5684c-315">String</span><span class="sxs-lookup"><span data-stu-id="5684c-315">String</span></span>|  
|<span data-ttu-id="5684c-316">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="5684c-316">INTEGRATED</span></span>|<span data-ttu-id="5684c-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="5684c-318">Zprostředkovatel OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="5684c-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="5684c-319">Oracle OLE DB ovladač Microsoft podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="5684c-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="5684c-320">Tabulky</span><span class="sxs-lookup"><span data-stu-id="5684c-320">Tables</span></span>  
  
- <span data-ttu-id="5684c-321">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-321">Columns</span></span>  
  
- <span data-ttu-id="5684c-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="5684c-322">Procedures</span></span>  
  
- <span data-ttu-id="5684c-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5684c-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="5684c-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5684c-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="5684c-325">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="5684c-325">Views</span></span>  
  
- <span data-ttu-id="5684c-326">Indexy</span><span class="sxs-lookup"><span data-stu-id="5684c-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="5684c-327">Tabulky</span><span class="sxs-lookup"><span data-stu-id="5684c-327">Tables</span></span>  
  
|<span data-ttu-id="5684c-328">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-328">ColumnName</span></span>|<span data-ttu-id="5684c-329">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-330">TABLE_CATALOG</span></span>|<span data-ttu-id="5684c-331">String</span><span class="sxs-lookup"><span data-stu-id="5684c-331">String</span></span>|  
|<span data-ttu-id="5684c-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="5684c-333">String</span><span class="sxs-lookup"><span data-stu-id="5684c-333">String</span></span>|  
|<span data-ttu-id="5684c-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-334">TABLE_NAME</span></span>|<span data-ttu-id="5684c-335">String</span><span class="sxs-lookup"><span data-stu-id="5684c-335">String</span></span>|  
|<span data-ttu-id="5684c-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-336">TABLE_TYPE</span></span>|<span data-ttu-id="5684c-337">String</span><span class="sxs-lookup"><span data-stu-id="5684c-337">String</span></span>|  
|<span data-ttu-id="5684c-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-338">TABLE_GUID</span></span>|<span data-ttu-id="5684c-339">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-339">Guid</span></span>|  
|<span data-ttu-id="5684c-340">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-340">DESCRIPTION</span></span>|<span data-ttu-id="5684c-341">String</span><span class="sxs-lookup"><span data-stu-id="5684c-341">String</span></span>|  
|<span data-ttu-id="5684c-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="5684c-342">TABLE_PROPID</span></span>|<span data-ttu-id="5684c-343">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-343">Int64</span></span>|  
|<span data-ttu-id="5684c-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5684c-344">DATE_CREATED</span></span>|<span data-ttu-id="5684c-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-345">DateTime</span></span>|  
|<span data-ttu-id="5684c-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5684c-346">DATE_MODIFIED</span></span>|<span data-ttu-id="5684c-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="5684c-348">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-348">Columns</span></span>  
  
|<span data-ttu-id="5684c-349">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-349">ColumnName</span></span>|<span data-ttu-id="5684c-350">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-351">TABLE_CATALOG</span></span>|<span data-ttu-id="5684c-352">String</span><span class="sxs-lookup"><span data-stu-id="5684c-352">String</span></span>|  
|<span data-ttu-id="5684c-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="5684c-354">String</span><span class="sxs-lookup"><span data-stu-id="5684c-354">String</span></span>|  
|<span data-ttu-id="5684c-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-355">TABLE_NAME</span></span>|<span data-ttu-id="5684c-356">String</span><span class="sxs-lookup"><span data-stu-id="5684c-356">String</span></span>|  
|<span data-ttu-id="5684c-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-357">COLUMN_NAME</span></span>|<span data-ttu-id="5684c-358">String</span><span class="sxs-lookup"><span data-stu-id="5684c-358">String</span></span>|  
|<span data-ttu-id="5684c-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-359">COLUMN_GUID</span></span>|<span data-ttu-id="5684c-360">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-360">Guid</span></span>|  
|<span data-ttu-id="5684c-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5684c-361">COLUMN_PROPID</span></span>|<span data-ttu-id="5684c-362">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-362">Int64</span></span>|  
|<span data-ttu-id="5684c-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5684c-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="5684c-364">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-364">Int64</span></span>|  
|<span data-ttu-id="5684c-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5684c-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="5684c-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-366">Boolean</span></span>|  
|<span data-ttu-id="5684c-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5684c-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="5684c-368">String</span><span class="sxs-lookup"><span data-stu-id="5684c-368">String</span></span>|  
|<span data-ttu-id="5684c-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5684c-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="5684c-370">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-370">Int64</span></span>|  
|<span data-ttu-id="5684c-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5684c-371">IS_NULLABLE</span></span>|<span data-ttu-id="5684c-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-372">Boolean</span></span>|  
|<span data-ttu-id="5684c-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-373">DATA_TYPE</span></span>|<span data-ttu-id="5684c-374">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-374">Int32</span></span>|  
|<span data-ttu-id="5684c-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-375">TYPE_GUID</span></span>|<span data-ttu-id="5684c-376">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-376">Guid</span></span>|  
|<span data-ttu-id="5684c-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5684c-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5684c-378">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-378">Int64</span></span>|  
|<span data-ttu-id="5684c-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5684c-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5684c-380">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-380">Int64</span></span>|  
|<span data-ttu-id="5684c-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5684c-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5684c-382">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-382">Int32</span></span>|  
|<span data-ttu-id="5684c-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5684c-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="5684c-384">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-384">Int16</span></span>|  
|<span data-ttu-id="5684c-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5684c-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="5684c-386">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-386">Int64</span></span>|  
|<span data-ttu-id="5684c-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="5684c-388">String</span><span class="sxs-lookup"><span data-stu-id="5684c-388">String</span></span>|  
|<span data-ttu-id="5684c-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="5684c-390">String</span><span class="sxs-lookup"><span data-stu-id="5684c-390">String</span></span>|  
|<span data-ttu-id="5684c-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="5684c-392">String</span><span class="sxs-lookup"><span data-stu-id="5684c-392">String</span></span>|  
|<span data-ttu-id="5684c-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="5684c-394">String</span><span class="sxs-lookup"><span data-stu-id="5684c-394">String</span></span>|  
|<span data-ttu-id="5684c-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="5684c-396">String</span><span class="sxs-lookup"><span data-stu-id="5684c-396">String</span></span>|  
|<span data-ttu-id="5684c-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-397">COLLATION_NAME</span></span>|<span data-ttu-id="5684c-398">String</span><span class="sxs-lookup"><span data-stu-id="5684c-398">String</span></span>|  
|<span data-ttu-id="5684c-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="5684c-400">String</span><span class="sxs-lookup"><span data-stu-id="5684c-400">String</span></span>|  
|<span data-ttu-id="5684c-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="5684c-402">String</span><span class="sxs-lookup"><span data-stu-id="5684c-402">String</span></span>|  
|<span data-ttu-id="5684c-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-403">DOMAIN_NAME</span></span>|<span data-ttu-id="5684c-404">String</span><span class="sxs-lookup"><span data-stu-id="5684c-404">String</span></span>|  
|<span data-ttu-id="5684c-405">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-405">DESCRIPTION</span></span>|<span data-ttu-id="5684c-406">String</span><span class="sxs-lookup"><span data-stu-id="5684c-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="5684c-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="5684c-407">Procedures</span></span>  
  
|<span data-ttu-id="5684c-408">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-408">ColumnName</span></span>|<span data-ttu-id="5684c-409">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5684c-411">String</span><span class="sxs-lookup"><span data-stu-id="5684c-411">String</span></span>|  
|<span data-ttu-id="5684c-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5684c-413">String</span><span class="sxs-lookup"><span data-stu-id="5684c-413">String</span></span>|  
|<span data-ttu-id="5684c-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="5684c-415">String</span><span class="sxs-lookup"><span data-stu-id="5684c-415">String</span></span>|  
|<span data-ttu-id="5684c-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5684c-417">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-417">Int16</span></span>|  
|<span data-ttu-id="5684c-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5684c-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="5684c-419">String</span><span class="sxs-lookup"><span data-stu-id="5684c-419">String</span></span>|  
|<span data-ttu-id="5684c-420">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-420">DESCRIPTION</span></span>|<span data-ttu-id="5684c-421">String</span><span class="sxs-lookup"><span data-stu-id="5684c-421">String</span></span>|  
|<span data-ttu-id="5684c-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5684c-422">DATE_CREATED</span></span>|<span data-ttu-id="5684c-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-423">DateTime</span></span>|  
|<span data-ttu-id="5684c-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5684c-424">DATE_MODIFIED</span></span>|<span data-ttu-id="5684c-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="5684c-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5684c-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="5684c-427">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-427">ColumnName</span></span>|<span data-ttu-id="5684c-428">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5684c-430">String</span><span class="sxs-lookup"><span data-stu-id="5684c-430">String</span></span>|  
|<span data-ttu-id="5684c-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5684c-432">String</span><span class="sxs-lookup"><span data-stu-id="5684c-432">String</span></span>|  
|<span data-ttu-id="5684c-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="5684c-434">String</span><span class="sxs-lookup"><span data-stu-id="5684c-434">String</span></span>|  
|<span data-ttu-id="5684c-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-435">COLUMN_NAME</span></span>|<span data-ttu-id="5684c-436">String</span><span class="sxs-lookup"><span data-stu-id="5684c-436">String</span></span>|  
|<span data-ttu-id="5684c-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-437">COLUMN_GUID</span></span>|<span data-ttu-id="5684c-438">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-438">Guid</span></span>|  
|<span data-ttu-id="5684c-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5684c-439">COLUMN_PROPID</span></span>|<span data-ttu-id="5684c-440">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-440">Int64</span></span>|  
|<span data-ttu-id="5684c-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="5684c-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="5684c-442">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-442">Int64</span></span>|  
|<span data-ttu-id="5684c-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5684c-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="5684c-444">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-444">Int64</span></span>|  
|<span data-ttu-id="5684c-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5684c-445">IS_NULLABLE</span></span>|<span data-ttu-id="5684c-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-446">Boolean</span></span>|  
|<span data-ttu-id="5684c-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-447">DATA_TYPE</span></span>|<span data-ttu-id="5684c-448">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-448">Int32</span></span>|  
|<span data-ttu-id="5684c-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-449">TYPE_GUID</span></span>|<span data-ttu-id="5684c-450">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-450">Guid</span></span>|  
|<span data-ttu-id="5684c-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5684c-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5684c-452">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-452">Int64</span></span>|  
|<span data-ttu-id="5684c-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5684c-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5684c-454">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-454">Int64</span></span>|  
|<span data-ttu-id="5684c-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5684c-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5684c-456">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-456">Int32</span></span>|  
|<span data-ttu-id="5684c-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5684c-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="5684c-458">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-458">Int16</span></span>|  
|<span data-ttu-id="5684c-459">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-459">DESCRIPTION</span></span>|<span data-ttu-id="5684c-460">String</span><span class="sxs-lookup"><span data-stu-id="5684c-460">String</span></span>|  
|<span data-ttu-id="5684c-461">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="5684c-461">OVERLOAD</span></span>|<span data-ttu-id="5684c-462">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="5684c-463">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="5684c-463">Views</span></span>  
  
|<span data-ttu-id="5684c-464">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-464">ColumnName</span></span>|<span data-ttu-id="5684c-465">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-466">TABLE_CATALOG</span></span>|<span data-ttu-id="5684c-467">String</span><span class="sxs-lookup"><span data-stu-id="5684c-467">String</span></span>|  
|<span data-ttu-id="5684c-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="5684c-469">String</span><span class="sxs-lookup"><span data-stu-id="5684c-469">String</span></span>|  
|<span data-ttu-id="5684c-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-470">TABLE_NAME</span></span>|<span data-ttu-id="5684c-471">String</span><span class="sxs-lookup"><span data-stu-id="5684c-471">String</span></span>|  
|<span data-ttu-id="5684c-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5684c-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="5684c-473">String</span><span class="sxs-lookup"><span data-stu-id="5684c-473">String</span></span>|  
|<span data-ttu-id="5684c-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="5684c-474">CHECK_OPTION</span></span>|<span data-ttu-id="5684c-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-475">Boolean</span></span>|  
|<span data-ttu-id="5684c-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="5684c-476">IS_UPDATABLE</span></span>|<span data-ttu-id="5684c-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-477">Boolean</span></span>|  
|<span data-ttu-id="5684c-478">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-478">DESCRIPTION</span></span>|<span data-ttu-id="5684c-479">String</span><span class="sxs-lookup"><span data-stu-id="5684c-479">String</span></span>|  
|<span data-ttu-id="5684c-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5684c-480">DATE_CREATED</span></span>|<span data-ttu-id="5684c-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-481">DateTime</span></span>|  
|<span data-ttu-id="5684c-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5684c-482">DATE_MODIFIED</span></span>|<span data-ttu-id="5684c-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="5684c-484">Indexy</span><span class="sxs-lookup"><span data-stu-id="5684c-484">Indexes</span></span>  
  
|<span data-ttu-id="5684c-485">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-485">ColumnName</span></span>|<span data-ttu-id="5684c-486">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-487">TABLE_CATALOG</span></span>|<span data-ttu-id="5684c-488">String</span><span class="sxs-lookup"><span data-stu-id="5684c-488">String</span></span>|  
|<span data-ttu-id="5684c-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="5684c-490">String</span><span class="sxs-lookup"><span data-stu-id="5684c-490">String</span></span>|  
|<span data-ttu-id="5684c-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-491">TABLE_NAME</span></span>|<span data-ttu-id="5684c-492">String</span><span class="sxs-lookup"><span data-stu-id="5684c-492">String</span></span>|  
|<span data-ttu-id="5684c-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-493">INDEX_CATALOG</span></span>|<span data-ttu-id="5684c-494">String</span><span class="sxs-lookup"><span data-stu-id="5684c-494">String</span></span>|  
|<span data-ttu-id="5684c-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="5684c-496">String</span><span class="sxs-lookup"><span data-stu-id="5684c-496">String</span></span>|  
|<span data-ttu-id="5684c-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-497">INDEX_NAME</span></span>|<span data-ttu-id="5684c-498">String</span><span class="sxs-lookup"><span data-stu-id="5684c-498">String</span></span>|  
|<span data-ttu-id="5684c-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="5684c-499">PRIMARY_KEY</span></span>|<span data-ttu-id="5684c-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-500">Boolean</span></span>|  
|<span data-ttu-id="5684c-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="5684c-501">UNIQUE</span></span>|<span data-ttu-id="5684c-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-502">Boolean</span></span>|  
|<span data-ttu-id="5684c-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="5684c-503">CLUSTERED</span></span>|<span data-ttu-id="5684c-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-504">Boolean</span></span>|  
|<span data-ttu-id="5684c-505">TYP</span><span class="sxs-lookup"><span data-stu-id="5684c-505">TYPE</span></span>|<span data-ttu-id="5684c-506">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-506">Int32</span></span>|  
|<span data-ttu-id="5684c-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="5684c-507">FILL_FACTOR</span></span>|<span data-ttu-id="5684c-508">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-508">Int32</span></span>|  
|<span data-ttu-id="5684c-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="5684c-509">INITIAL_SIZE</span></span>|<span data-ttu-id="5684c-510">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-510">Int32</span></span>|  
|<span data-ttu-id="5684c-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="5684c-511">NULLS</span></span>|<span data-ttu-id="5684c-512">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-512">Int32</span></span>|  
|<span data-ttu-id="5684c-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="5684c-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="5684c-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-514">Boolean</span></span>|  
|<span data-ttu-id="5684c-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="5684c-515">AUTO_UPDATE</span></span>|<span data-ttu-id="5684c-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-516">Boolean</span></span>|  
|<span data-ttu-id="5684c-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="5684c-517">NULL_COLLATION</span></span>|<span data-ttu-id="5684c-518">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-518">Int32</span></span>|  
|<span data-ttu-id="5684c-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5684c-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="5684c-520">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-520">Int64</span></span>|  
|<span data-ttu-id="5684c-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-521">COLUMN_NAME</span></span>|<span data-ttu-id="5684c-522">String</span><span class="sxs-lookup"><span data-stu-id="5684c-522">String</span></span>|  
|<span data-ttu-id="5684c-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-523">COLUMN_GUID</span></span>|<span data-ttu-id="5684c-524">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-524">Guid</span></span>|  
|<span data-ttu-id="5684c-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5684c-525">COLUMN_PROPID</span></span>|<span data-ttu-id="5684c-526">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-526">Int64</span></span>|  
|<span data-ttu-id="5684c-527">KOLACE</span><span class="sxs-lookup"><span data-stu-id="5684c-527">COLLATION</span></span>|<span data-ttu-id="5684c-528">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-528">Int16</span></span>|  
|<span data-ttu-id="5684c-529">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="5684c-529">CARDINALITY</span></span>|<span data-ttu-id="5684c-530">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="5684c-530">Decimal</span></span>|  
|<span data-ttu-id="5684c-531">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="5684c-531">PAGES</span></span>|<span data-ttu-id="5684c-532">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-532">Int32</span></span>|  
|<span data-ttu-id="5684c-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="5684c-533">FILTER_CONDITION</span></span>|<span data-ttu-id="5684c-534">String</span><span class="sxs-lookup"><span data-stu-id="5684c-534">String</span></span>|  
|<span data-ttu-id="5684c-535">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="5684c-535">INTEGRATED</span></span>|<span data-ttu-id="5684c-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="5684c-537">Zprostředkovatel Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="5684c-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="5684c-538">Microsoft Jet OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="5684c-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="5684c-539">Tabulky</span><span class="sxs-lookup"><span data-stu-id="5684c-539">Tables</span></span>  
  
- <span data-ttu-id="5684c-540">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-540">Columns</span></span>  
  
- <span data-ttu-id="5684c-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="5684c-541">Procedures</span></span>  
  
- <span data-ttu-id="5684c-542">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="5684c-542">Views</span></span>  
  
- <span data-ttu-id="5684c-543">Indexy</span><span class="sxs-lookup"><span data-stu-id="5684c-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="5684c-544">Tabulky</span><span class="sxs-lookup"><span data-stu-id="5684c-544">Tables</span></span>  
  
|<span data-ttu-id="5684c-545">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-545">ColumnName</span></span>|<span data-ttu-id="5684c-546">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-547">TABLE_CATALOG</span></span>|<span data-ttu-id="5684c-548">String</span><span class="sxs-lookup"><span data-stu-id="5684c-548">String</span></span>|  
|<span data-ttu-id="5684c-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="5684c-550">String</span><span class="sxs-lookup"><span data-stu-id="5684c-550">String</span></span>|  
|<span data-ttu-id="5684c-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-551">TABLE_NAME</span></span>|<span data-ttu-id="5684c-552">String</span><span class="sxs-lookup"><span data-stu-id="5684c-552">String</span></span>|  
|<span data-ttu-id="5684c-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-553">TABLE_TYPE</span></span>|<span data-ttu-id="5684c-554">String</span><span class="sxs-lookup"><span data-stu-id="5684c-554">String</span></span>|  
|<span data-ttu-id="5684c-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-555">TABLE_GUID</span></span>|<span data-ttu-id="5684c-556">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-556">Guid</span></span>|  
|<span data-ttu-id="5684c-557">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-557">DESCRIPTION</span></span>|<span data-ttu-id="5684c-558">String</span><span class="sxs-lookup"><span data-stu-id="5684c-558">String</span></span>|  
|<span data-ttu-id="5684c-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="5684c-559">TABLE_PROPID</span></span>|<span data-ttu-id="5684c-560">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-560">Int64</span></span>|  
|<span data-ttu-id="5684c-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5684c-561">DATE_CREATED</span></span>|<span data-ttu-id="5684c-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-562">DateTime</span></span>|  
|<span data-ttu-id="5684c-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5684c-563">DATE_MODIFIED</span></span>|<span data-ttu-id="5684c-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="5684c-565">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-565">Columns</span></span>  
  
|<span data-ttu-id="5684c-566">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-566">ColumnName</span></span>|<span data-ttu-id="5684c-567">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-568">TABLE_CATALOG</span></span>|<span data-ttu-id="5684c-569">String</span><span class="sxs-lookup"><span data-stu-id="5684c-569">String</span></span>|  
|<span data-ttu-id="5684c-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="5684c-571">String</span><span class="sxs-lookup"><span data-stu-id="5684c-571">String</span></span>|  
|<span data-ttu-id="5684c-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-572">TABLE_NAME</span></span>|<span data-ttu-id="5684c-573">String</span><span class="sxs-lookup"><span data-stu-id="5684c-573">String</span></span>|  
|<span data-ttu-id="5684c-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-574">COLUMN_NAME</span></span>|<span data-ttu-id="5684c-575">String</span><span class="sxs-lookup"><span data-stu-id="5684c-575">String</span></span>|  
|<span data-ttu-id="5684c-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-576">COLUMN_GUID</span></span>|<span data-ttu-id="5684c-577">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-577">Guid</span></span>|  
|<span data-ttu-id="5684c-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5684c-578">COLUMN_PROPID</span></span>|<span data-ttu-id="5684c-579">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-579">Int64</span></span>|  
|<span data-ttu-id="5684c-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5684c-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="5684c-581">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-581">Int64</span></span>|  
|<span data-ttu-id="5684c-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5684c-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="5684c-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-583">Boolean</span></span>|  
|<span data-ttu-id="5684c-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5684c-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="5684c-585">String</span><span class="sxs-lookup"><span data-stu-id="5684c-585">String</span></span>|  
|<span data-ttu-id="5684c-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5684c-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="5684c-587">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-587">Int64</span></span>|  
|<span data-ttu-id="5684c-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5684c-588">IS_NULLABLE</span></span>|<span data-ttu-id="5684c-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-589">Boolean</span></span>|  
|<span data-ttu-id="5684c-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-590">DATA_TYPE</span></span>|<span data-ttu-id="5684c-591">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-591">Int32</span></span>|  
|<span data-ttu-id="5684c-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-592">TYPE_GUID</span></span>|<span data-ttu-id="5684c-593">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-593">Guid</span></span>|  
|<span data-ttu-id="5684c-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5684c-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5684c-595">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-595">Int64</span></span>|  
|<span data-ttu-id="5684c-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5684c-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5684c-597">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-597">Int64</span></span>|  
|<span data-ttu-id="5684c-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5684c-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5684c-599">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-599">Int32</span></span>|  
|<span data-ttu-id="5684c-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5684c-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="5684c-601">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-601">Int16</span></span>|  
|<span data-ttu-id="5684c-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5684c-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="5684c-603">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-603">Int64</span></span>|  
|<span data-ttu-id="5684c-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="5684c-605">String</span><span class="sxs-lookup"><span data-stu-id="5684c-605">String</span></span>|  
|<span data-ttu-id="5684c-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="5684c-607">String</span><span class="sxs-lookup"><span data-stu-id="5684c-607">String</span></span>|  
|<span data-ttu-id="5684c-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="5684c-609">String</span><span class="sxs-lookup"><span data-stu-id="5684c-609">String</span></span>|  
|<span data-ttu-id="5684c-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="5684c-611">String</span><span class="sxs-lookup"><span data-stu-id="5684c-611">String</span></span>|  
|<span data-ttu-id="5684c-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="5684c-613">String</span><span class="sxs-lookup"><span data-stu-id="5684c-613">String</span></span>|  
|<span data-ttu-id="5684c-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-614">COLLATION_NAME</span></span>|<span data-ttu-id="5684c-615">String</span><span class="sxs-lookup"><span data-stu-id="5684c-615">String</span></span>|  
|<span data-ttu-id="5684c-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="5684c-617">String</span><span class="sxs-lookup"><span data-stu-id="5684c-617">String</span></span>|  
|<span data-ttu-id="5684c-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="5684c-619">String</span><span class="sxs-lookup"><span data-stu-id="5684c-619">String</span></span>|  
|<span data-ttu-id="5684c-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-620">DOMAIN_NAME</span></span>|<span data-ttu-id="5684c-621">String</span><span class="sxs-lookup"><span data-stu-id="5684c-621">String</span></span>|  
|<span data-ttu-id="5684c-622">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-622">DESCRIPTION</span></span>|<span data-ttu-id="5684c-623">String</span><span class="sxs-lookup"><span data-stu-id="5684c-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="5684c-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="5684c-624">Procedures</span></span>  
  
|<span data-ttu-id="5684c-625">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-625">ColumnName</span></span>|<span data-ttu-id="5684c-626">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5684c-628">String</span><span class="sxs-lookup"><span data-stu-id="5684c-628">String</span></span>|  
|<span data-ttu-id="5684c-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5684c-630">String</span><span class="sxs-lookup"><span data-stu-id="5684c-630">String</span></span>|  
|<span data-ttu-id="5684c-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="5684c-632">String</span><span class="sxs-lookup"><span data-stu-id="5684c-632">String</span></span>|  
|<span data-ttu-id="5684c-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5684c-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5684c-634">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-634">Int16</span></span>|  
|<span data-ttu-id="5684c-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5684c-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="5684c-636">String</span><span class="sxs-lookup"><span data-stu-id="5684c-636">String</span></span>|  
|<span data-ttu-id="5684c-637">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-637">DESCRIPTION</span></span>|<span data-ttu-id="5684c-638">String</span><span class="sxs-lookup"><span data-stu-id="5684c-638">String</span></span>|  
|<span data-ttu-id="5684c-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5684c-639">DATE_CREATED</span></span>|<span data-ttu-id="5684c-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-640">DateTime</span></span>|  
|<span data-ttu-id="5684c-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5684c-641">DATE_MODIFIED</span></span>|<span data-ttu-id="5684c-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="5684c-643">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="5684c-643">Views</span></span>  
  
|<span data-ttu-id="5684c-644">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-644">ColumnName</span></span>|<span data-ttu-id="5684c-645">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-646">TABLE_CATALOG</span></span>|<span data-ttu-id="5684c-647">String</span><span class="sxs-lookup"><span data-stu-id="5684c-647">String</span></span>|  
|<span data-ttu-id="5684c-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="5684c-649">String</span><span class="sxs-lookup"><span data-stu-id="5684c-649">String</span></span>|  
|<span data-ttu-id="5684c-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-650">TABLE_NAME</span></span>|<span data-ttu-id="5684c-651">String</span><span class="sxs-lookup"><span data-stu-id="5684c-651">String</span></span>|  
|<span data-ttu-id="5684c-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5684c-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="5684c-653">String</span><span class="sxs-lookup"><span data-stu-id="5684c-653">String</span></span>|  
|<span data-ttu-id="5684c-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="5684c-654">CHECK_OPTION</span></span>|<span data-ttu-id="5684c-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-655">Boolean</span></span>|  
|<span data-ttu-id="5684c-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="5684c-656">IS_UPDATABLE</span></span>|<span data-ttu-id="5684c-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-657">Boolean</span></span>|  
|<span data-ttu-id="5684c-658">POPIS</span><span class="sxs-lookup"><span data-stu-id="5684c-658">DESCRIPTION</span></span>|<span data-ttu-id="5684c-659">String</span><span class="sxs-lookup"><span data-stu-id="5684c-659">String</span></span>|  
|<span data-ttu-id="5684c-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5684c-660">DATE_CREATED</span></span>|<span data-ttu-id="5684c-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-661">DateTime</span></span>|  
|<span data-ttu-id="5684c-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5684c-662">DATE_MODIFIED</span></span>|<span data-ttu-id="5684c-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="5684c-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="5684c-664">Indexy</span><span class="sxs-lookup"><span data-stu-id="5684c-664">Indexes</span></span>  
  
|<span data-ttu-id="5684c-665">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="5684c-665">ColumnName</span></span>|<span data-ttu-id="5684c-666">DataType</span><span class="sxs-lookup"><span data-stu-id="5684c-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5684c-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-667">TABLE_CATALOG</span></span>|<span data-ttu-id="5684c-668">String</span><span class="sxs-lookup"><span data-stu-id="5684c-668">String</span></span>|  
|<span data-ttu-id="5684c-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="5684c-670">String</span><span class="sxs-lookup"><span data-stu-id="5684c-670">String</span></span>|  
|<span data-ttu-id="5684c-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-671">TABLE_NAME</span></span>|<span data-ttu-id="5684c-672">String</span><span class="sxs-lookup"><span data-stu-id="5684c-672">String</span></span>|  
|<span data-ttu-id="5684c-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5684c-673">INDEX_CATALOG</span></span>|<span data-ttu-id="5684c-674">String</span><span class="sxs-lookup"><span data-stu-id="5684c-674">String</span></span>|  
|<span data-ttu-id="5684c-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5684c-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="5684c-676">String</span><span class="sxs-lookup"><span data-stu-id="5684c-676">String</span></span>|  
|<span data-ttu-id="5684c-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-677">INDEX_NAME</span></span>|<span data-ttu-id="5684c-678">String</span><span class="sxs-lookup"><span data-stu-id="5684c-678">String</span></span>|  
|<span data-ttu-id="5684c-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="5684c-679">PRIMARY_KEY</span></span>|<span data-ttu-id="5684c-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-680">Boolean</span></span>|  
|<span data-ttu-id="5684c-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="5684c-681">UNIQUE</span></span>|<span data-ttu-id="5684c-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-682">Boolean</span></span>|  
|<span data-ttu-id="5684c-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="5684c-683">CLUSTERED</span></span>|<span data-ttu-id="5684c-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-684">Boolean</span></span>|  
|<span data-ttu-id="5684c-685">TYP</span><span class="sxs-lookup"><span data-stu-id="5684c-685">TYPE</span></span>|<span data-ttu-id="5684c-686">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-686">Int32</span></span>|  
|<span data-ttu-id="5684c-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="5684c-687">FILL_FACTOR</span></span>|<span data-ttu-id="5684c-688">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-688">Int32</span></span>|  
|<span data-ttu-id="5684c-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="5684c-689">INITIAL_SIZE</span></span>|<span data-ttu-id="5684c-690">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-690">Int32</span></span>|  
|<span data-ttu-id="5684c-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="5684c-691">NULLS</span></span>|<span data-ttu-id="5684c-692">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-692">Int32</span></span>|  
|<span data-ttu-id="5684c-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="5684c-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="5684c-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-694">Boolean</span></span>|  
|<span data-ttu-id="5684c-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="5684c-695">AUTO_UPDATE</span></span>|<span data-ttu-id="5684c-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-696">Boolean</span></span>|  
|<span data-ttu-id="5684c-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="5684c-697">NULL_COLLATION</span></span>|<span data-ttu-id="5684c-698">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-698">Int32</span></span>|  
|<span data-ttu-id="5684c-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5684c-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="5684c-700">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-700">Int64</span></span>|  
|<span data-ttu-id="5684c-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5684c-701">COLUMN_NAME</span></span>|<span data-ttu-id="5684c-702">String</span><span class="sxs-lookup"><span data-stu-id="5684c-702">String</span></span>|  
|<span data-ttu-id="5684c-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5684c-703">COLUMN_GUID</span></span>|<span data-ttu-id="5684c-704">Guid</span><span class="sxs-lookup"><span data-stu-id="5684c-704">Guid</span></span>|  
|<span data-ttu-id="5684c-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5684c-705">COLUMN_PROPID</span></span>|<span data-ttu-id="5684c-706">Int64</span><span class="sxs-lookup"><span data-stu-id="5684c-706">Int64</span></span>|  
|<span data-ttu-id="5684c-707">KOLACE</span><span class="sxs-lookup"><span data-stu-id="5684c-707">COLLATION</span></span>|<span data-ttu-id="5684c-708">Int16</span><span class="sxs-lookup"><span data-stu-id="5684c-708">Int16</span></span>|  
|<span data-ttu-id="5684c-709">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="5684c-709">CARDINALITY</span></span>|<span data-ttu-id="5684c-710">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="5684c-710">Decimal</span></span>|  
|<span data-ttu-id="5684c-711">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="5684c-711">PAGES</span></span>|<span data-ttu-id="5684c-712">Int32</span><span class="sxs-lookup"><span data-stu-id="5684c-712">Int32</span></span>|  
|<span data-ttu-id="5684c-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="5684c-713">FILTER_CONDITION</span></span>|<span data-ttu-id="5684c-714">String</span><span class="sxs-lookup"><span data-stu-id="5684c-714">String</span></span>|  
|<span data-ttu-id="5684c-715">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="5684c-715">INTEGRATED</span></span>|<span data-ttu-id="5684c-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="5684c-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5684c-717">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5684c-717">See also</span></span>

- [<span data-ttu-id="5684c-718">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="5684c-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
