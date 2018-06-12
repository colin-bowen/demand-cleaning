# demand-cleaning
sorting demand for inputting into TEPES


%call files to check node agreement

filename = "SpanishPortuguese_400kV_Location_PowerGrid1";
sheetnodos = "Nodos-Localizacion";
node_name = xlsread(filename,sheetnodos,"A2:A305");
node_id = xlsread(filename, sheetnodos, "B2:B305");
node_location = xlsread(filename, sheetnodos, "C2:D305");

% call demand files

filename2 = "SpanishPortuguese_Demand(400 +220)
sheet = "Hoja1";
demand_node_id = xlsread(filename2, sheet, "B1:B1538");
demand_node = xlsread(filename2, sheet, "C1:C1538");

%merge node demand into one

demand = [demand_node_id, demand_node];

demand = sort(demand, 1);

demand_total = zeros(length(unique(demand_node_id)),1);
i = 1;
j = 1;
while i <=length(demand)
  demand_total(i) = demand(j);
  if demand(i) ~= demand(i+1)
    i = i+1;
    j = j+1;
  else
   j = j + 1;
  end
end
